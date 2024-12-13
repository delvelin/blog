---
title:  "How it Works"
layout: post
categories: media
---

## **Introduction**

**Delveline** is a Code Vulnerability Analyzer for Java and Kotlin that supports best practices in security and risk management.  
By aligning with ISO/IEC 27001 principles, Delveline helps raise security awareness and improve software development security.


## **How it Works**

![delvelin process](https://delvelin.github.io/assets/img/delvelin-diagram-transparent.png?raw=true)

**Delveline Code Vulnerability Analysis Workflow**

1. **Input Source Code**
   
    - **Using Delvelin Plugin** : The user installs the Delveline plugin or library into the 
      project using Gradle or 
   Maven. If the user chooses to use the Delveline plugin, it will run in Gradle with a task 
   called `delvelinScan`. 
    - **Using delvelin Library**: If the user opts for the library, they must run Delveline from 
      a unit test.

   - **Using Gitlab CI** : The user can also run Delveline in a GitLab CI pipeline.

2. **Delveline Analysis with Two Approaches**
   - 2.1. **Static Analysis for Allowed File Types** (By default: .java, .kt, .gradle, .kts, and 
     .xml). The following vulnerabilities are checked:
     - **Multi-thread Safety Check**
          - Analyzes to detect the use of non-thread-safe data structures such as `HashMap`, `ArrayList`, etc., in multi-threading scenarios.

     - **Sensitive Data Detection**
          - Delveline scans the source code to detect hardcoded sensitive data, such as:
              - API Tokens
              - Passwords
              - Private Keys
     - **Weak Cryptographic Detection**
       - Detects whether there are weak cryptographic algorithms in the code such as : MD5, SHA-1, 
         DES, DESede (Triple DES), RC4, Blowfish, RSA with key sizes of 512, 1024, or 1536 bits, 
         DSA with key sizes of 512, 1024, or 1536 bits and HMAC-MD5
       
     - **SQL Injection Detection**
       - Detects queries in the source code that may be vulnerable to SQL injection.

     - **XSS Vulnerability Scan**
          - Analyzes XSS patterns using regex on the code strings to detect potential vulnerabilities.

     - **CWE Reference Integration**
          - The analysis results are linked to the vulnerability list from CWE (Common Weakness Enumeration) to provide the appropriate vulnerability categories.

     - **CVSS Scoring**
         - Delveline uses the CVSS (Common Vulnerability Scoring System) to score the severity and prioritize fixing vulnerabilities.

     - **Dependency Vulnerability Detection (OSV.dev)**
         - Delveline scans the project for outdated or vulnerable dependencies with the help of the OSV.dev database.

     - **Generate Analysis Report**
       - Delveline generates a final report that includes:
         - Details of the vulnerabilities found
         - Severity score based on CVSS
         - Recommendations for remediation

   - 2.2. **Analyze Libraries/Dependencies Used in the Project**
     Delveline checks the .gradle, .kts, or .xml files for any listed dependencies that have known vulnerabilities in OSV.dev.

3. **Results Display**  
   After completing the two analysis approaches, the results will be displayed in the form of a LOG, JSON, or HTML, depending on the user's configuration.  
   **Note:** For GitLab CI, only LOG output is available.