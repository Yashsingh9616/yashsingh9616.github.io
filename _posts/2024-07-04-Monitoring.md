---
 layout: post
 title: Monitoring
---

 - Monitoring refers to the process of observing and checking the status and performance of systems, applications, 
   networks, or any other IT infrastructure components. The primary goal of monitoring is to ensure that these systems are functioning correctly, detect any issues or anomalies promptly, and gather data for performance analysis and optimization.
 

 - **Black Box Monitoring:**

   - Black-box monitoring is a way to check how well a system is working by looking at it from the outside, without
     knowing what’s happening inside. It focuses on monitoring outputs and behaviors visible from an external viewpoint, such as response times, error rates, or availability.


    - Simple Explanation:

     - External View: Imagine you're watching a movie. You judge the movie based on what you see and hear, not by 
       reading the script or knowing how it was made. Similarly, black box monitoring looks at the system's outputs and behaviors from the outside.

     - Website Monitoring: Regularly sending requests to a website to check if pages load correctly and quickly.
                           If the homepage takes too long to load, you know there’s a problem, even if you don’t know why.

     - API Monitoring: Sending requests to an API and checking the responses. If the API returns errors or takes too 
                       long to respond, you identify an issue based on the observed behavior.

     - Server Uptime Monitoring: Checking if a server is up and running by pinging it. If the server doesn’t 
                                 respond, you know there’s a problem without needing to understand the server’s internal processes.


 - **White Box Monitoring**

   - White Box Monitoring is a method of observing and evaluating a system's performance and health from an internal
     perspective. It involves having full access to the system's internal workings, such as code, infrastructure, and internal metrics.

   - Internal Metrics: It tracks internal metrics such as CPU usage, memory consumption, disk I/O, database query 
                       performance, and other low-level operational data.

   - Resource Utilization: Monitoring resource utilization helps ensure that resources (like servers, databases,
                           or network connections) are used efficiently and are not overloaded.

   -  Deeper Insights: This helps you find and fix issues more easily because you have detailed information about 
                       the system’s operations.

     - **Example**
       - Web applications:
         - White-box monitoring can monitor parameters like the number of active users, requests to access user 
           profiles, and requests to post comments. It can also monitor HTTP handlers and usage logs.


 - **Push Based Monitoring**

   - Push-based monitoring is like students (services/systems) regularly updating the teacher (monitoring system) 
     about their progress without being asked. The students (services/systems) take the initiative to report their status and metrics to the teacher (monitoring system).

   
   - (1). Website Monitoring
      -   A website is configured to send a status update to a monitoring tool every minute. The website (student) 
         sends a message to the monitoring tool (teacher) saying, “I’m online, and my load time is 1 second.” 
        
        
   - (2). Server Monitoring
          A server is set up to automatically report its CPU and memory usage to a monitoring system every five minutes. The server (student) sends an update to the monitoring system (teacher), “I’m using 40% CPU and 60% memory.”


 - **Pull Based Monitoring**
   - Pull-based monitoring is like a teacher checking in on students regularly to see how they’re doing. The teacher 
     (monitoring system) goes around the classroom (services/systems) and asks each student (service/system) how they’re doing (their status and metrics).


    - (1). Website Monitoring
      - Imagine a monitoring tool that checks your website every minute to see if it’s online and how fast it’s 
        loading. The tool (teacher) asks the website (student) every minute, “Are you up? How fast are you loading?” 

        
    - (2). Server Monitoring
      - A monitoring system regularly checks the status of a server to see how much CPU and memory it’s using. The 
        system (teacher) asks the server (student) every five minutes, “How much CPU are you using? How much memory are you using?” In both examples, the monitoring system is actively checking (pulling information) from the services to gather data about their current status.
   