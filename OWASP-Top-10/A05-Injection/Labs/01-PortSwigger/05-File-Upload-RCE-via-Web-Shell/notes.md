# Notes — Remote Code Execution via Web Shell Upload

## Lab

PortSwigger Web Security Academy — Remote code execution via web shell upload.

## Objective

Demonstrate how an insecure file upload mechanism can allow an attacker-controlled PHP file to be uploaded and executed by the web server.

## Vulnerability

The avatar upload functionality does not adequately restrict executable server-side files. A PHP file can therefore be uploaded and accessed from a web-accessible location.

## Workflow

1. Authenticate to the lab application.
2. Navigate to the avatar upload functionality.
3. Prepare a PHP test payload.
4. Intercept the upload request using Burp Suite.
5. Upload the PHP file through the avatar functionality.
6. Observe the uploaded file location.
7. Request the uploaded PHP resource.
8. Confirm server-side execution from the response.
9. Verify that the PortSwigger lab is solved.

## Key Evidence

- `screenshots/01-authentication.png`
- `screenshots/02-php-payload.png`
- `screenshots/03-file-upload-success.png`
- `screenshots/04-burp-upload-request.png`
- `screenshots/05-rce-lab-solved.png`

## Burp Evidence

- `burp/upload-request.txt`
- `burp/uploaded-file-request.txt`

## Security Impact

If an application permits executable server-side files to be uploaded and executed, an attacker may achieve remote code execution with the privileges of the web application process.

Potential impact includes:

- Unauthorized access to application data
- Exposure of sensitive files
- Modification or deletion of application files
- Further compromise of the application environment

## Defensive Takeaways

- Use a strict server-side allowlist for permitted file types.
- Validate actual file content, not only the filename.
- Generate server-side filenames instead of trusting user-controlled names.
- Store uploaded files outside the web root where practical.
- Disable script execution in upload directories.
- Apply least-privilege permissions to the web server.
- Enforce file-size and resource limits.
- Monitor suspicious upload activity.

## Learning Outcome

The key lesson is that secure file-upload handling requires more than checking whether a file can be uploaded.

The application must also ensure that uploaded content cannot become executable server-side code.