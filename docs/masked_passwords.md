# Using custom encrypted passwords
This guide is intended for setting up custom encrypted passwords in a basic single node installation, 
turning on masked passwords, configuring a custom password codec class, and verifying the deployment.


## Prepare a basic single node installation
a. Install Your Application: If you haven't already, install your application on a single node. This typically involves downloading the application's installation package or using package managers like apt or yum for Linux-based systems or using an installer for Windows. Follow the specific installation instructions provided for your application.

 

b. Basic Configuration: During the installation process, you might be prompted to configure your application. Ensure that you provide basic configuration parameters such as the database connection details, URLs, and any other settings required for your application to work correctly.

 

c. Start Your Application: After installation and initial configuration, start your application. This is usually done by running a command or service specific to your application. Ensure that your application is up and running without errors.

 

## Turn masked passwords on
a. Locate Configuration Files: Identify the configuration files used by your application. These files typically contain sensitive data like database connection strings or API keys. Common examples include 'config.yml', 'application.properties', or '.env files'.


b. Edit the Configuration File: Open the configuration file with a text editor. Locate the password-related properties, which may look something like this: 
("db_password: mysecretpassword")


c. Enable Masked Passwords: To enable masked passwords, modify these properties by adding '!vault |' in front of the password values. For example:
("db_password: !vault | AG2asf9saf...")
The value following '|' should be an encoded or encrypted version of your actual password.

 

d. Store Encrypted Passwords: Store the encrypted passwords securely. You can use a tool like HashiCorp Vault or a custom encryption method to generate these masked passwords.

 

## Configure a custom password codec class
a. Design a Custom Codec Class: Develop a custom password codec class that will be responsible for secure password encryption and verification. This class should include well-defined methods for hashing and verifying passwords and should adhere to best coding practices.

b.  Select Hashing Algorithms: Choose a robust cryptographic hashing algorithm for password storage, such as bcrypt, Argon2, or scrypt. These algorithms are designed to resist brute force and dictionary attacks and provide a high level of security.

c. Integration: Integrate your custom password codec class seamlessly with your application’s existing authentication system. This typically involves modifying your login and registration processes to utilize the custom class for password-related operations.

d. Configuration Management: Safeguard the configuration details of your custom codec class. This includes the specific algorithm used, its parameters, and any salt or initialization vectors. Properly managing these details is essential for successfully verifying passwords.

 

## Verify deployment

a. Testing: Implement thorough testing of your password management system. Create a variety of test cases that encompass password creation, hashing, and verification. Verify that each component of your system works as intended.

b. Security Testing: Conduct security testing, including penetration testing and code reviews, to identify vulnerabilities and potential weaknesses in your password management system. Address any issues promptly to maintain robust security.

c. Performance Testing: Monitor the performance of your application after implementing encrypted passwords. Ensure that the encryption and decryption processes do not significantly impact your system’s speed and responsiveness.

d. Continuous Maintenance: Regularly review and update your custom password codec class and security measures. Stay informed about the latest security best practices and keep abreast of updates to your chosen hashing algorithms to protect your system against emerging threats.
