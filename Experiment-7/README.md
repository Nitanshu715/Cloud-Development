# CAD Experiment 7: Introduction to Amazon API Gateway
 
## 1. Experiment Details
- **Course:** Cloud Application Development (CAD)
- **Experiment:** 7 — Introduction to Amazon API Gateway
- **AWS Region:** `ap-south-1` (Asia Pacific — Mumbai)
- **REST API:** `CAD-Experiment-7-REST-API`
- **API ID:** `6pnwbvfcy6`
- **Lambda function:** `cad-exp7-student-api`
- **Resource:** `/students`
- **Methods:** `GET`, `POST`
- **Deployment stage:** `dev`
 
## 2. Aim
To create and deploy a REST API using Amazon API Gateway, integrate GET and POST methods with AWS Lambda, test the endpoint, configure API-key-based access, and review logs and metrics in Amazon CloudWatch.
 
## 3. Learning Outcomes
- Understand REST APIs, resources, methods, deployment stages, and invoke URLs.
- Integrate API Gateway methods with Lambda using Lambda proxy integration.
- Deploy and test an HTTPS endpoint.
- Configure an API key and usage plan for basic access control.
- Inspect API execution logs and monitoring metrics in CloudWatch.
 
## 4. Architecture
```text
Client / PowerShell
        |
        | HTTPS GET or POST
        v
Amazon API Gateway REST API
  Resource: /students
  Stage: dev
        |
        | Lambda proxy integration
        v
AWS Lambda: cad-exp7-student-api
        |
        v
Amazon CloudWatch Logs and Metrics
```
 
## 5. Resources
| Resource | Value |
|---|---|
| REST API | `CAD-Experiment-7-REST-API` |
| API ID | `6pnwbvfcy6` |
| Lambda function | `cad-exp7-student-api` |
| Resource path | `/students` |
| Methods | `GET`, `POST` |
| Integration | Lambda proxy integration |
| Stage | `dev` |
| Usage plan | `CAD-Experiment-7-Usage-Plan` |
| API key name | `CAD-Experiment-7-Key` |
| API Gateway log group | `API-Gateway-Execution-Logs_6pnwbvfcy6/dev` |
| Lambda log group | `/aws/lambda/cad-exp7-student-api` |
 
## 6. Invoke URL
```text
https://6pnwbvfcy6.execute-api.ap-south-1.amazonaws.com/dev/students
```
 
Protected requests require the API key in the `x-api-key` header. Never commit an API key to a public repository.
 
## 7. Intended Lambda Implementation
The following code documents the intended student API behavior. Ensure the Lambda runtime handler points to the file and function containing this code, and deploy the code.
 
```python
import json
 
STUDENTS = [
    {"id": 1, "name": "Aarav"},
    {"id": 2, "name": "Diya"}
]
 
def lambda_handler(event, context):
    method = (
        event.get("httpMethod")
        or event.get("requestContext", {}).get("http", {}).get("method")
        or "GET"
    )
 
    if method == "GET":
        return {
            "statusCode": 200,
            "headers": {"Content-Type": "application/json"},
            "body": json.dumps({"students": STUDENTS})
        }
 
    if method == "POST":
        raw_body = event.get("body") or "{}"
        try:
            body = json.loads(raw_body) if isinstance(raw_body, str) else raw_body
        except (json.JSONDecodeError, TypeError):
            return {
                "statusCode": 400,
                "headers": {"Content-Type": "application/json"},
                "body": json.dumps({"error": "Invalid JSON"})
            }
 
        name = body.get("name") if isinstance(body, dict) else None
        if not isinstance(name, str) or not name.strip():
            return {
                "statusCode": 400,
                "headers": {"Content-Type": "application/json"},
                "body": json.dumps({"error": "The 'name' field is required"})
            }
 
        student = {"id": len(STUDENTS) + 1, "name": name.strip()}
        STUDENTS.append(student)
        return {
            "statusCode": 201,
            "headers": {"Content-Type": "application/json"},
            "body": json.dumps({
                "message": "Student created",
                "student": student
            })
        }
 
    return {
        "statusCode": 405,
        "headers": {"Content-Type": "application/json"},
        "body": json.dumps({"error": "Method not allowed"})
    }
```
 
**Verification note:** During the final tests, Lambda and API Gateway continued returning `Hello from Lambda!`, including for POST requests. Therefore, the student-specific behavior shown above was not verified as working. Check the Lambda handler configuration (for example, whether it still points to `index.handler` instead of the Python handler) before reporting those responses as successful.
 
## 8. API Gateway Setup
1. Select the AWS region `ap-south-1`.
2. Create/open the REST API `CAD-Experiment-7-REST-API`.
3. Create the `/students` resource.
4. Add `GET` and `POST` methods.
5. Configure each method for Lambda proxy integration with `cad-exp7-student-api`.
6. Deploy the API to the `dev` stage.
7. Use the invoke URL above followed by `/students`.
 
## 9. PowerShell Tests
Set the endpoint and your own API key. Do not store real keys in this README.
 
```powershell
$baseUrl = "https://6pnwbvfcy6.execute-api.ap-south-1.amazonaws.com/dev/students"
$apiKey = "<YOUR_API_KEY>"
$headers = @{ "x-api-key" = $apiKey }
```
 
### GET
```powershell
Invoke-RestMethod -Method GET -Uri $baseUrl -Headers $headers
```
**Expected with the intended handler:** HTTP `200`, with a JSON student list.
 
**Observed:** With the API key supplied, the request reached Lambda but returned `Hello from Lambda!`; the student-list response was not verified.
 
### POST — valid JSON
```powershell
$body = @{ name = "Riya" } | ConvertTo-Json
Invoke-RestMethod -Method POST -Uri $baseUrl -Headers $headers -ContentType "application/json" -Body $body
```
**Expected with the intended handler:** HTTP `201`, with the created student.
 
**Observed:** The endpoint returned `Hello from Lambda!`; student creation was not verified.
 
### POST — missing name
```powershell
$body = @{ age = 21 } | ConvertTo-Json
Invoke-RestMethod -Method POST -Uri $baseUrl -Headers $headers -ContentType "application/json" -Body $body
```
**Expected with the intended handler:** HTTP `400`, with a missing-name error.
 
### POST — invalid JSON
```powershell
Invoke-RestMethod -Method POST -Uri $baseUrl -Headers $headers -ContentType "application/json" -Body '{"name":'
```
**Expected with the intended handler:** HTTP `400`, with an invalid-JSON error.
 
### API-key authorization
```powershell
Invoke-RestMethod -Method GET -Uri $baseUrl
```
**Observed:** A request without the required API key returned HTTP `403`. CloudWatch reported that the API key was required but missing or not associated with a usage plan. Supplying the configured key in `x-api-key` allowed the request to reach the integration.
 
## 10. API Key and Usage Plan
1. Create usage plan `CAD-Experiment-7-Usage-Plan`.
2. Associate the deployed `dev` stage with the plan.
3. Create API key `CAD-Experiment-7-Key`.
4. Associate the key with the usage plan.
5. Require an API key on the methods intended to be protected.
6. Send the key in the `x-api-key` header.
 
An API key supports usage-plan enforcement but is not a replacement for strong authentication and authorization. Keep keys secret and rotate or delete exposed keys.
 
## 11. CloudWatch Monitoring
**Log groups**
- API Gateway: `API-Gateway-Execution-Logs_6pnwbvfcy6/dev`
- Lambda: `/aws/lambda/cad-exp7-student-api`
 
**Procedure**
1. Open CloudWatch in `ap-south-1`.
2. Go to **Logs → Log groups**.
3. Inspect API Gateway logs for request, authorization, and integration errors.
4. Inspect Lambda logs for invocation output and exceptions.
5. Review API Gateway stage metrics for available request, latency, and error metrics.
6. If the response is unexpected, verify the Lambda handler, deployed code, API integration target, and stage deployment.
 
**Troubleshooting**
- **403 without a key:** Check method API-key requirements, key association, usage plan, and stage association.
- **Unexpected `Hello from Lambda!`:** Verify that the Lambda handler points to the updated code. Another file, such as `index.mjs`, may still be configured as the handler.
- **Changes not reflected:** Deploy the Lambda code and redeploy API Gateway after API configuration changes.
- **Logs missing:** Confirm logging is enabled and the execution role has required CloudWatch permissions.
 
## 12. Results
- Created a REST API in the Mumbai AWS region.
- Configured `/students` with GET and POST methods.
- Integrated both methods with Lambda proxy integration.
- Deployed the API to the `dev` stage and identified the invoke URL.
- Configured API-key-based access using a usage plan.
- Tested requests from PowerShell and inspected CloudWatch logs.
- Confirmed that requests without the required API key returned HTTP `403`.
- **Limitation:** The final observed Lambda/API response remained `Hello from Lambda!`; the intended student-specific GET/POST logic was not verified.
 
## 13. Cleanup
After saving screenshots and the report, delete only resources created specifically for this experiment if they are no longer needed:
- REST API `CAD-Experiment-7-REST-API` (`6pnwbvfcy6`)
- Lambda function `cad-exp7-student-api`
- Usage plan `CAD-Experiment-7-Usage-Plan`
- API key `CAD-Experiment-7-Key`
- API Gateway log group `API-Gateway-Execution-Logs_6pnwbvfcy6/dev`
- Lambda log group `/aws/lambda/cad-exp7-student-api`
- An IAM role only if it was created solely for this lab and is unused elsewhere
 
Do not delete shared IAM roles, policies, or resources used by other projects. The API key was exposed during troubleshooting; delete or rotate it if it still exists.
 
## 14. Conclusion
This experiment covered exposing a Lambda function through Amazon API Gateway, deploying a REST API, invoking GET and POST methods, configuring API-key and usage-plan controls, and reviewing CloudWatch logs. API-key authorization was observed working as expected. The Lambda handler mismatch that caused the default `Hello from Lambda!` response must be corrected before the student-specific GET/POST behavior can be reported as fully functional.
