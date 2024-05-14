# Configuring WSO2 API Manager to Accept Untrusted Backend Certificates (Development Only)
Important Note: This guide outlines steps to configure WSO2 API Manager (APIM) to accept untrusted backend certificates. This configuration is intended for development or testing environments only and should not be used in production. Using this configuration bypasses security measures and makes your system vulnerable to potential security risks like man-in-the-middle attacks.

# Scenario:

You have a backend server with a self-signed certificate or a certificate signed by an untrusted Certificate Authority (CA).
You want to establish a TLS connection between WSO2 APIM and the backend server for secure communication.
Steps:

# Adding Certificate to Backend (Optional):

If your backend server uses a self-signed certificate, you might need to add it to the trusted certificate store of your system or application that interacts with the backend. Refer to the documentation for your backend server for specific instructions on adding trusted certificates.
Adjusting WSO2 APIM Configuration (Not Recommended for Production):

Warning: This step weakens security. Proceed only if you understand the risks and are working in a development environment.

# Edit the deployment.toml file located at:
---
/home/wso2carbon/wso2am-3.2.0/repository/conf/deployment.toml
---
# Add the following configuration snippet under the [transport.passthru_https.sender.parameters] section:
---
Ini, TOML
HostnameVerifier = "AllowAll"
---
Use code with caution.
content_copy
# Save the changes to the deployment.toml file.

Restarting WSO2 APIM Container:

Restart the container hosting your WSO2 APIM instance. The specific method for restarting the container depends on your containerization platform (e.g., Docker). Refer to the documentation for your platform for instructions on restarting containers.
Expected Outcome:

After restarting WSO2 APIM, it should be able to establish a TLS connection with the backend server even if the backend certificate is not trusted by the system.
