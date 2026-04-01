# Deptain
Detain and analyze project npm, pypi, and more dependencies in a fast and safe manner before they reach your machine.

Supply chain attacks have alwaYs been an issue but particularly in 2026, the effects have been aggregious. Deptain seeks to prevent the millions of users, servers, and production environments that will inevitably download third-party dependencies from package managers such as NPM, PyPi, and more from being infected by polluted software supply chains. 

## POC
Such a tool seeks to wrap existing package manager CLI tools such as NPM. A containerized or sandboxed instance is spun up and installs a project's dependencies (e.g. from `package-lock.json`) in that environment separately from the host machine. The tool will:
- Analyze any source code if possible
- Read and monitor any pre/post installation scripts
- Monitor network traffic for any suspicious network requests
- Be easy to use and have little to no hassle over simply performing an install command
- Provide analytics and traceability to suspect code
- more as the tool gets more sophisticated...

Once the user confirms, the environment will be torn down and the dependencies installed on the real host device.

To work best with automated systems such as CI/CD pipelines, the tool will output a score along with any suspicious files and/or network requests in which an admin can verify. Admins can set their score threshold for how "dangerous" they are willing to accept an automated install with no human intervention. 

Some of the solutions this might *not* solve yet with the current requirements are:
- Dormant Trojans that do not call out to home in the time the container is running
- Obfuscated code in repositories where obfuscation is common (such as decompiled proprietary code or encryption-heavy projects)
- Malicious code that is installed pre-compiled
- Possibly some more...

There are some similarities and planned usage of code from a previous [project](https://github.com/d0w/supplychainattack-research)

**NOTE**: I am not a security researcher and am not responsible for any issues nor assumptions this project may cause. I have a strong passion for cybersecurity and am seeking solutions to the current climate of software development (let's not even talk about AI...). 
