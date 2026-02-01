# Log Archival & System Performance Optimization

## Business Problem
The SOAP log and API log tables had grown extremely large, with approximately **1.7 crore (17 million)** and **3 crore (30 million)** records respectively. Queries for tracing logs involved **complex joins**, resulting in execution times exceeding **40 seconds**. This severely impacted **application performance and responsiveness**, making it difficult for operations teams to troubleshoot and monitor transactions effectively.

## Business Objectives
- **Reduce query execution time** for log tracing and monitoring.  
- **Improve overall application performance**.  
- **Ensure compliance** by retaining at least **90 days of logs** in the source database.  
- **Maintain data integrity** during the archival process.  

## My Role (Business Analyst Perspective)
- **Problem Analysis:** Identified the large volume of logs as the key performance bottleneck.  
- **Solution Planning:** Proposed an archival strategy to migrate older logs to a separate **audit database** while retaining recent data.  
- **Collaboration:** Worked closely with the **DBA team** to design the workflow, batch sizes, and verification process.  
- **Requirement Validation:** Validated that each batch of archived records was correctly stored before deletion from the source database.  
- **Process Oversight:** Defined retention rules and batch sizes, ensuring **FIFO (First In, First Out)** processing in batches of **40,000 records**.  
- **Scheduler & Automation:** Oversaw creation of **jobs and scheduling** to automate archival, ensuring minimal impact on system performance.  

## Solution & Workflow
1. **Batch Selection:** Logs are selected in batches of **400,000 records** from source tables (SOAP log and API log).  
2. **Archival:** Each batch is inserted into the **Audit Log Database**.  
3. **Verification:** System verifies that all selected records are present in the audit database.  
4. **Deletion:** Only after successful verification are records deleted from the source database.  
5. **Retention Policy:** Ensure that the **last 90 days of logs** remain in the source tables.  
6. **Automation:** Scheduled jobs run the archival workflow regularly to maintain system performance.  

## Outcome
- Query execution time for log tracing reduced from **>40 seconds to <10 seconds**.  
- Significant improvement in **overall application performance**.  
- **Data retention and compliance rules** fully respected.  

## Success Metrics / Impact
- **Reduced log query execution time by 75%+**.  
- Enabled operations teams to **trace logs faster and more reliably**.  
- **Improved application stability and responsiveness** during peak usage.  

## Key Learnings
- Collaboration between **BA and DBA teams** is critical for balancing performance, compliance, and operational stability.  
- Proper **batch processing and verification** prevents data loss and ensures system reliability.  
- **Data retention policies** must be integrated into technical solutions to meet compliance requirements.  
- Anticipating **system bottlenecks** and designing workflows proactively can greatly improve user experience.
