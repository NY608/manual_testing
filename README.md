Manual and Performance Testing for Login Page - bstackdemo.com
Objective:
To ensure the functionality, performance, and compatibility of the login page on bstackdemo.com through comprehensive manual and performance testing. Bug reports are also documented.

Testing Overview:
The tests are categorized as follows:

Functional Testing: Covering positive and negative scenarios, boundary value analysis, and user experience validation across devices.
Mobile Testing: Tested across various mobile device resolutions to ensure responsive design and usability.
Performance Testing: Conducted using JMeter and BlazeMeter to measure response times, throughput, and identify performance bottlenecks.
Security Testing: Validated for secure login, password handling, and session management.
Browser Compatibility: Ensured functionality across multiple browsers, including Chrome, Firefox, Safari, and Edge

Tools Used:
Manual Testing: Documented using Excel for test case creation and tracking.
Performance Testing: Scripts developed and executed in JMeter, with load and stress tests performed using BlazeMeter.

Performance Test Conclusion:
Objective:
The test assessed the performance and responsiveness of the login page on bstackdemo.com under simulated user loads, focusing on throughput, response times, and system stability.

Summary of Results: for 5 concurrent users.

Average Response Time: 396.2 ms, showing efficient handling of requests with minimal delay under tested load.
90th Percentile Response Time: 463 ms, indicating that 90% of requests were processed within a reasonable time frame, showcasing stability.
Throughput: 12.1 hits/s, demonstrating the system's ability to handle concurrent user activity effectively.
andwidth: Average bandwidth of 340.12 KiB/s, supporting smooth data transfer.
Error Rate: 0%, highlighting robust stability and reliability during the test.
Engine Health: No errors or system resource issues were observed in the load engines, confirming the reliability of the test environment.

### Performance Test Conclusion (20-User Load)

**Objective:**  
This 20-user load test evaluated the resilience and response stability of the login page under increased user concurrency.

**Summary of Results:**  
- **Response Times**: Consistent with prior tests, average response times were within acceptable limits.
- **Error Rate and Types**:
  - **SSLException**: 2 instances of socket closure, likely due to session handling under load.
  - **NoHttpResponseException**: 1 instance where the server did not respond, suggesting possible server overload or configuration limits.
  - **ConnectionClosedException**: 2 instances of premature content length closure, indicating partial responses potentially due to server strain.

**Conclusions and Recommendations**:  
To enhance stability:
- **SSL Configuration**: Review and tune SSL settings to handle concurrent sessions smoothly.
- **Connection Handling**: Ensure server configurations can handle higher loads without premature closures.
- **Error Monitoring**: Establish regular monitoring to quickly address intermittent connectivity issues under increased traffic.

This test indicates reliable performance under load but highlights areas for improvement to ensure uninterrupted service during peak times.

### Performance Test Conclusion (50-User Load)

**Objective:**  
This test simulated 50 concurrent users to assess the scalability of the login page, focusing on response times, throughput, and error handling.

**Summary of Results:**  
- **Response Times**: The average response time was 384.24 ms, with 90% of requests completing within 401 ms, which is within an acceptable range for this load level.
- **Throughput**: Achieved an average throughput of 103.12 hits/s, demonstrating strong handling of concurrent requests.
- **Bandwidth**: Average bandwidth of 2.83 MiB/s, supporting efficient data handling.
- **Error Rate**: Minimal errors (0.01%), with two main error types:
  - **ConnectionClosedException**: 1 instance of a premature content end.
  - **SocketException**: 1 instance of socket closure, indicating possible network or session handling issues.

**Conclusions and Recommendations**:  
While the application performs well under load, error instances suggest a need for minor tuning:
- **Session Management**: Address connection handling for better consistency during peak usage.
- **Network Resilience**: Configure socket handling to reduce premature closures under load spikes.

In summary, the application handles 50 concurrent users efficiently, with only slight improvements needed for peak load stability.

Response Time Measurement Script for bstackdemo.com
Description:
This PowerShell script measures the response time for the login page at bstackdemo.com. It captures:

Time to Connect: The content length of the response in KB.
Time to First Byte: Timestamp of the first byte received.
Time to First Byte: Timestamp of the first byte received.
Total Time: Total response time in milliseconds.
Requirements:
PowerShell: Installed on your system (PowerShell 5 or later recommended).
Internet Connection: Required to access the website URL.
script:-
# Define the URI
$uri = "https://bstackdemo.com/signin"

# Measure the response time
$requestTime = Measure-Command {
    $response = Invoke-WebRequest -Uri $uri
}

# Output the results
Write-Output "Time to Connect: $($response.RawContentLength / 1KB) KB"
Write-Output "Time to First Byte: $($response.Headers.'Date')"
Write-Output "Total Time: $($requestTime.TotalMilliseconds) ms"
Instructions
Copy the above script into a PowerShell .ps1 file (e.g., ResponseTimeCheck.ps1).
Run the script in PowerShell:
.\ResponseTimeCheck.ps1

