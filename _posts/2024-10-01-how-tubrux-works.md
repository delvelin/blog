---
layout: post
---

## How Tubrux Works: A Hybrid Approach to Vulnerability Analysis

**Tubrux** is a **runtime-assisted static analysis tool** designed to detect potential vulnerabilities in Java and Kotlin codebases. 

Unlike traditional Static Application Security Testing (SAST) tools, which perform code analysis without execution, Tubrux requires the code to be run in a runtime environment—either within the main application or a unit test. The tool works by first gathering the source code from the project, including files like `.java`, `.kt`,`.gradle` and `.xml`. 

Once executed, Tubrux analyzes the code, looking for issues such as thread-safety violations, deadlocks, and sensitive data exposure. This execution phase allows Tubrux to incorporate runtime context into its analysis, making it a **hybrid analyzer** rather than a pure static analysis tool.

By combining static code reading with runtime behavior, Tubrux is able to detect a broader range of vulnerabilities, particularly those that only manifest during code execution, thus offering more comprehensive vulnerability detection than traditional SAST tools.

Here’s the flow diagram of **Tubrux**'s process in text format, describing its operation as a **runtime-assisted static analysis tool** or **hybrid analyzer**:

```html
+----------------------------------------+
|  Start: Project Code Base              |
+----------------------------------------+
                   |
                   v
+----------------------------------------+
|  Step 1: Gather Source                 |
|  Code Files (.java, .kt, .gradle, ...) |
+----------------------------------------+
                   |
                   v
+----------------------------------------+
|  Step 2: Run Tubrux                    |
|  (Executed in Main App or Unit Test)   |
+----------------------------------------+
                   |
                   v
+----------------------------------------+
|  Step 3: Analyze Code                  |
|  (Hybrid: Static & Runtime)            |
+----------------------------------------+
                   |
                   v
+----------------------------------------+
|  Step 4: Identify Issues               |
|  (e.g., thread-safety, deadlocks,      |
|   sensitive data)                      |
+----------------------------------------+
                   |
                   v
+----------------------------------------+
|  Step 5: Report Findings               |
|  (Vulnerability Report)                |
+----------------------------------------+
                   |
                   v
+----------------------------------------+
|                 End                    |
+----------------------------------------+
```

1. **Start**: The process begins with gathering the **source code files** from the project (e.g., `.java`, `.kt`, `.gradle`).
2. **Step 1**: Tubrux collects code from various files for analysis.
3. **Step 2**: **Tubrux is executed**, either in the main application or within a unit test, to start the execution and analysis.
4. **Step 3**: At this stage, **Tubrux analyzes the code**, combining static code inspection with runtime information gathered during execution.
5. **Step 4**: **Issues are detected**, such as **thread-safety** violations, **deadlocks**, and **sensitive data exposure**.
6. **Step 5**: The analysis results are **reported**, generating a vulnerability report that highlights potential problems in the code.
7. **End**: The process concludes with the report providing valuable insights for fixing vulnerabilities.

With this workflow, Tubrux is classified as a **runtime-assisted static analysis tool** or **hybrid analyzer**, as it requires code execution to complete its analysis, blending both static and dynamic aspects for vulnerability detection.

<img src="https://github.com/tubrux/blog/blob/dark/_posts/example-output.png?raw=true"/>

Tubrux offers a convenient and user-friendly approach to reviewing detected issues by providing **clickable log reports**. When an analysis is completed, Tubrux generates a **detailed vulnerability report** that not only highlights the type and nature of each potential issue—such as thread-safety risks, deadlocks, or sensitive data exposure—but also provides **direct links** to the specific lines in the source code where these issues are detected.

### Key Benefits of Tubrux's Log Report:
1. **Clickable Code Navigation**:
   - Each reported issue includes a link to the exact file and line number in the source code.
   - By simply clicking on these links, users can immediately navigate to the problematic line, saving time and effort in locating issues manually.

2. **Clear and Structured Information**:
   - Tubrux logs are designed to be readable, with clear categorization of issue types and concise descriptions of each vulnerability.
   - The report format makes it easy for developers to prioritize and address high-impact issues efficiently.

3. **Faster Debugging and Resolution**:
   - With direct links to code, developers can instantly review and modify the code around the reported line, facilitating a smoother debugging process.
   - This direct access shortens the feedback loop, allowing developers to apply fixes and rerun analyses in real time.

By offering these navigable logs, Tubrux enhances productivity and minimizes time spent searching for vulnerabilities, making it an invaluable tool for streamlined code review and issue resolution.
