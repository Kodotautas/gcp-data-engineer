Data Engineer Practice Exam
===========================

##### You are building storage for files for a data pipeline on Google Cloud. You want to support JSON files. The schema of these files will occasionally change. Your analyst teams will use running aggregate ANSI SQL queries on this data. What should you do?

A. Use BigQuery for storage. Provide format files for data load. Update the format files as needed.

B. Use BigQuery for storage. Select "Automatically detect" in the Schema section.

C. Use Cloud Storage for storage. Link data as temporary tables in BigQuery and turn on the "Automatically detect" option in the Schema section of BigQuery.

D. Use Cloud Storage for storage. Link data as permanent tables in BigQuery and turn on the "Automatically detect" option in the Schema section of BigQuery.

---
Feedback

B (Correct Answer) - B is correct because of the requirement to support occasionally (schema) changing JSON files and aggregate ANSI SQL queries: you need to use BigQuery, and it is quickest to use 'Automatically detect' for schema changes.

A is not correct because you should not provide format files: you can simply turn on the 'Automatically detect' schema changes flag.

C and D are not correct because you should not use Cloud Storage for this scenario: it is cumbersome and doesn't add value.

---

##### Your infrastructure includes two 100-TB enterprise file servers. You need to perform a one-way, one-time migration of this data to the Google Cloud securely. Only users in Germany will access this data. You want to create the most cost-effective solution. What should you do?

A. Use Transfer Appliance to transfer the offsite backup files to a Cloud Storage Regional storage bucket as a final destination.

B. Use Transfer Appliance to transfer the offsite backup files to a Cloud Storage Multi-Regional bucket as a final destination.

C. Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Regional storage bucket as a final destination.

D. Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Multi-Regional storage bucket as a final destination.

---

Feedback

A (Correct Answer) - A is correct because you are performing a one-time (rather than an ongoing series) data transfer from on-premises to Google Cloud Platform for users in a single region (Germany). Using a Regional storage bucket will reduce cost and also conform to regulatory requirements.

B, C, and D are not correct because you should only use Transfer Service for a one-time one-way transfer (C,D) and because you should not use a Multi-Regional storage bucket for users in a single region (B,D). Also, Storage Transfer Service does not work for data stored on-premises.

---
##### Your infrastructure runs on another cloud and includes a set of multi-TB enterprise databases that are backed up nightly both on premises and also to that cloud. You need to create a redundant backup to Google Cloud. You are responsible for performing scheduled monthly disaster recovery drills. You want to create a cost-effective solution. What should you do?

A. Use Transfer Appliance to transfer the offsite backup files to a Cloud Storage Nearline storage bucket as a final destination.

B. Use Transfer Appliance to transfer the offsite backup files to a Cloud Storage Coldline bucket as a final destination.

C. Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Nearline storage bucket as a final destination.

D. Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Coldline storage bucket as a final destination.

---

Feedback

C (Correct Answer) - C is correct because you will need to access your backup data monthly to test your disaster recovery process, so you should use a Nearline bucket; also because you will be performing ongoing, regular data transfers, so you should use the storage transfer service.

A, B, and D are not correct because you should not use Coldline if you want to access the files monthly (B,D) and you should not use Transfer Appliance for repeated data transfers (A,B).

---

##### You are designing a relational data repository on Google Cloud to grow as needed. The data will be transactionally consistent and added from any location in the world. You want to monitor and adjust node count for input traffic, which can spike unpredictably. What should you do?

A. Use Cloud Spanner for storage. Monitor storage usage and increase node count if more than 70% utilized.

B. Use Cloud Spanner for storage. Monitor CPU utilization and increase node count if more than 70% utilized for your time span.

C. Use Cloud Bigtable for storage. Monitor data stored and increase node count if more than 70% utilized.

D. Use Cloud Bigtable for storage. Monitor CPU utilization and increase node count if more than 70% utilized for your time span.

---

Feedback

B (Correct Answer) - B is correct because of the requirement to globally scalable transactions---use Cloud Spanner. CPU utilization is the recommended metric for scaling, per Google best practices, linked below.

A is not correct because you should not use storage utilization as a scaling metric.

C, D are not correct because you should not use Cloud Bigtable for this scenario.

---

##### You have 250,000 devices which produce a JSON device status event every 10 seconds. You want to capture this event data for outlier time series analysis. What should you do?

A. Ship the data into BigQuery. Develop a custom application that uses the BigQuery API to query the dataset and displays device outlier data based on your business requirements.

B. Ship the data into BigQuery. Use the BigQuery console to query the dataset and display device outlier data based on your business requirements.

C. Ship the data into Cloud Bigtable. Use the Cloud Bigtable cbt tool to display device outlier data based on your business requirements.

D. Ship the data into Cloud Bigtable. Install and use the HBase shell for Cloud Bigtable to query the table for device outlier data based on your business requirements.

---

Feedback

C (Correct Answer) - C is correct because the data type, volume, and query pattern best fits BigTable capabilities and also Google best practices as linked below.

A and B are not correct because you do not need to use BigQuery for the query pattern in this scenario.

D is not correct because you can use the simpler method of 'cbt tool' to support this scenario.

---

##### You are designing storage for event data as part of building a data pipeline on Google Cloud. Your input data is in CSV format. You want to minimize the cost of querying individual values over time windows. Which storage service and schema design should you use?

A. Use Cloud Bigtable for storage. Design tall and narrow tables, and use a new row for each single event version.

B. Use Cloud Bigtable for storage. Design short and wide tables, and use a new column for each single event version.

C. Use Cloud Storage for storage. Join the raw file data with a BigQuery log table.

D. Use Cloud Storage for storage. Write a Cloud Dataprep job to split the data into partitioned tables.

---

Feedback

A (Correct Answer) - A is correct because it is a recommended Google practice; see the link below. Use Cloud Bigtable and this schema for this scenario.

B is not correct because you should design tall and narrow tables, not short and wide tables, and also because you should use a new row, not a new column, for this scenario.

C and D are not correct because you do not need to use GCS/BQ for this scenario.

---

##### You are selecting a streaming service for log messages that must include final result message ordering as part of building a data pipeline on Google Cloud. You want to stream input for 5 days and be able to query the most recent message value. You will be storing the data in a searchable repository. How should you set up the input messages?

A. Use Cloud Pub/Sub for input. Attach a timestamp to every message in the publisher.

B. Use Cloud Pub/Sub for input. Attach a unique identifier to every message in the publisher.

C. Use Apache Kafka on Compute Engine for input. Attach a timestamp to every message in the publisher.

D. Use Apache Kafka on Compute Engine for input. Attach a unique identifier to every message in the publisher.

---

Feedback

A (Correct Answer) - A is correct because of recommended Google practices; see the links below.

B is not correct because you should not attach a GUID to each message to support the scenario.

C and D are not correct because you should not use Apache Kafka for this scenario (it is overly complex compared to using Cloud Pub/Sub, which can support all of the requirements).

---

##### You are designing storage for CSV files and using an I/O-intensive custom Apache Spark transform as part of deploying a data pipeline on Google Cloud. You are using ANSI SQL to run queries for your analysts. You want to support complex aggregate queries and reuse existing code. How should you transform the input data?

A. Use BigQuery for storage. Use Cloud Dataflow to run the transformations.

B. Use BigQuery for storage. Use Cloud Dataproc to run the transformations.

C. Use Cloud Storage for storage. Use Cloud Dataflow to run the transformations.

D. Use Cloud Storage for storage. Use Cloud Dataproc to run the transformations.

---

Feedback

B (Correct Answer) - B is correct because of the requirement to use custom Spark transforms; use Cloud Dataproc. ANSI SQL queries require the use of BigQuery.

A is not correct because you should not use Cloud Dataflow for this scenario.

C and D are not correct because you should not use Cloud Storage for this scenario, and you should also not use Cloud Dataflow. Instead, you should just add secondary indexes.

---

##### You are building a data pipeline on Google Cloud. You need to select services that will host a deep neural network machine-learning model also hosted on Google Cloud. You also need to monitor and run jobs that could occasionally fail. What should you do?

A. Use Cloud Machine Learning to host your model. Monitor the status of the Operation object for 'error' results.

B. Use Cloud Machine Learning to host your model. Monitor the status of the Jobs object for 'failed' job states.

C. Use a Kubernetes Engine cluster to host your model. Monitor the status of the Jobs object for 'failed' job states.

D. Use a Kubernetes Engine cluster to host your model. Monitor the status of Operation object for 'error' results.

---

Feedback

B (Correct Answer) - B is correct because of the requirement to host an ML DNN and Google-recommended monitoring object (Jobs); see the links below.

A is not correct because you should not use the Operation object to monitor failures.

C and D are not correct because you should not use a Kubernetes Engine cluster for this scenario.

---

##### You are building a data pipeline on Google Cloud. You need to prepare source data for a machine-learning model. This involves quickly deduplicating rows from three input tables and also removing outliers from data columns where you do not know the data distribution. What should you do?

A. Write an Apache Spark job with a series of steps for Cloud Dataflow. The first step will examine the source data, and the second and third steps step will perform data transformations.

B. Write an Apache Spark job with a series of steps for Cloud Dataproc. The first step will examine the source data, and the second and third steps step will perform data transformations.

C. Use Cloud Dataprep to preview the data distributions in sample source data table columns. Write a recipe to transform the data and add it to the Cloud Dataprep job.

D. Use Cloud Dataprep to preview the data distributions in sample source data table columns. Click on each column name, click on each appropriate suggested transformation, and then click 'Add' to add each transformation to the Cloud Dataprep job.

---

Feedback

D (Correct Answer) - D is correct because of the requirements to prepare/clean source data: use Cloud Dataprep suggested transformations to quickly build a transformation job.

C is not correct because you should not write a recipe in Cloud Dataprep: you can simply use the suggested transformations.

A and B are not correct because you should not use Apache Spark and Cloud Dataflow or Cloud Dataproc for this scenario.

---

##### You need to deploy a TensorFlow machine-learning model to Google Cloud. You want to maximize the speed and minimize the cost of model prediction and deployment. What should you do?

A. Export your trained model to a SavedModel format. Deploy and run your model on Cloud ML Engine.

B. Export your trained model to a SavedModel format. Deploy and run your model from a Kubernetes Engine cluster.

C. Export 2 copies of your trained model to a SavedModel format. Store artifacts in Cloud Storage. Run 1 version on CPUs and another version on GPUs.

D. Export 2 copies of your trained model to a SavedModel format. Store artifacts in Cloud ML Engine. Run 1 version on CPUs and another version on GPUs.

---

Feedback

A (Correct Answer) - A is correct because of Google recommended practices; that is, "just deploy it."

B is not correct because you should not run your model from Kubernetes Engine.

C and D are not correct because you should not export 2 copies of your trained model, etc, for this scenario.

---

##### You have data stored in a Cloud Storage dataset and also in a BigQuery dataset. You need to secure the data and provide 3 different types of access levels for your Google Cloud Platform users: administrator, read/write, and read-only. You want to follow Google-recommended practices.What should you do?

A. Create 3 custom IAM roles with appropriate policies for the access levels needed for Cloud Storage and BigQuery. Add your users to the appropriate roles.

B. At the Organization level, add your administrator user accounts to the Owner role, add your read/write user accounts to the Editor role, and add your read-only user accounts to the Viewer role.

C. At the Project level, add your administrator user accounts to the Owner role, add your read/write user accounts to the Editor role, and add your read-only user accounts to the Viewer role.

D. Use the appropriate pre-defined IAM roles for each of the access levels needed for Cloud Storage and BigQuery. Add your users to those roles for each of the services.

---

Feedback

D (Correct Answer) - D is correct because the principle of least privilege favors using pre-created roles with associated policies when they match your requirements.

A, B, and C are not correct because it is a Google best practice to use pre-defined IAM roles when they exist and match your business scenario; see the links below.

---

##### You are developing an application on Google Cloud that will label famous landmarks in users' photos. You are under competitive pressure to develop the predictive model quickly. You need to keep service costs low. What should you do?

A. Build an application that calls the Cloud Vision API. Inspect the generated MID values to supply the image labels.

B. Build an application that calls the Cloud Vision API. Pass landmark locations as base64-encoded strings.

C. Build and train a classification model with TensorFlow. Deploy the model using Cloud Machine Learning Engine. Pass landmark locations as base64-encoded strings.

D. Build and train a classification model with TensorFlow. Deploy the model using Cloud Machine Learning Engine. Inspect the generated MID values to supply the image labels.

---

Feedback

B (Correct Answer) - B is correct because of the requirement to quickly develop a model that generates landmark labels from photos. This is supported in Cloud Vision API; see the link below.

A is not correct because you should not inspect the generated MID values; instead, you should simply pass the image locations to the API and use the labels, which are output.

C and D are not correct because you should not build a custom classification TF model for this scenario.

---

##### You are setting up Cloud Dataproc to perform some data transformations using Apache Spark jobs. The data will be used for a new set of non-critical experiments in your marketing group. You want to set up a cluster that can transform a large amount of data in the most cost-effective way. What should you do?

A. Set up a cluster in High Availability mode with high-memory machine types. Add 10 additional local SSDs.

B. Set up a cluster in High Availability mode with default machine types. Add 10 additional Preemptible worker nodes.

C. Set up a cluster in Standard mode with high-memory machine types. Add 10 additional Preemptible worker nodes.

D. Set up a cluster in Standard mode with the default machine types. Add 10 additional local SSDs.

---

Feedback

C (Correct Answer) - C is correct because Spark and high-memory machines only need the Standard mode.

Also, use Preemptible nodes because you want to save money and this is not mission-critical.

A and B are not correct because this scenario does not call for High Availability mode.

D is not correct because you should not add more local SSDs; instead, use Preemptible nodes to meet your objective of delivering a cost-effective solution.

---

##### You are upgrading your existing (development) Cloud Bigtable instance for use in your production environment. The instance contains a large amount of data that you want to make available for production immediately. You need to design for fastest performance. What should you do?

A. Change your Cloud Bigtable instance type from Development to Production, and set the number of nodes to at least 3. Verify that the storage type is HDD.

B. Change your Cloud Bigtable instance type from Development to Production, and set the number of nodes to at least 3. Verify that the storage type is SSD.

C. Export the data from your current Cloud Bigtable instance to Cloud Storage. Create a new Cloud Bigtable Production instance type with at least 3 nodes. Select the HDD storage type. Import the data into the new instance from Cloud Storage.

D. Export the data from your current Cloud Bigtable instance to Cloud Storage. Create a new Cloud Bigtable Production instance type with at least 3 nodes. Select the SSD storage type. Import the data into the new instance from Cloud Storage.

---

Feedback

B (Correct Answer) - B is correct because Cloud Bigtable allows you to 'scale-in-place,' which meets your requirements for this scenario.

A is not correct because you should be using SSD storage for this scenario.

C and D are not correct because creating a new Cloud Bigtable instance is extraneous and not needed to export, you can upgrade in place for nodes, but the storage type cannot be changed.

---
xxxxxxxxxxxxx
##### As part of your backup plan, you set up regular snapshots of Compute Engine instances that are running. You want to be able to restore these snapshots using the fewest possible steps for replacement instances. What should you do?

A. Export the snapshots to Cloud Storage. Create disks from the exported snapshot files. Create images from the new disks.

B. Export the snapshots to Cloud Storage. Create images from the exported snapshot files.

C. Use the snapshots to create replacement disks. Use the disks to create instances as needed.

D. Use the snapshots to create replacement instances as needed.

---

Feedback

D (Correct Answer) - D is correct because the scenario asks how to recreate instances.

A, B, and C are not correct because the Google best practice of creating images from running Compute Engine instances is to first take a snapshot, export it to Cloud Storage, and then import that file as the basis for a custom image for use in DR scenarios; see the link below.

---

##### You regularly use prefetch caching with a Data Studio report to visualize the results of BigQuery queries. You want to minimize service costs. What should you do?

A. Set up the report to use the Owner's credentials to access the underlying data in BigQuery, and direct the users to view the report only once per business day (24-hour period).

B. Set up the report to use the Owner's credentials to access the underlying data in BigQuery, and verify that the 'Enable cache' checkbox is selected for the report.

C. Set up the report to use the Viewer's credentials to access the underlying data in BigQuery, and also set it up to be a 'view-only' report.

D. Set up the report to use the Viewer's credentials to access the underlying data in BigQuery, and verify that the 'Enable cache' checkbox is not selected for the report.

---

Feedback

B (Correct Answer) - B is correct because you must set Owner credentials to use the 'enable cache' option in BigQuery. It is also a Google best practice to use the 'enable cache' option when the business scenario calls for using prefetch caching.

A, C, and D are not correct because a cache auto-expires every 12 hours; a prefetch cache is only for data sources that use the Owner's credentials (not the Viewer's credentials).

---

##### You want to display aggregate view counts for your YouTube channel data in Data Studio. You want to see the video tiles and view counts summarized over the last 30 days. You also want to segment the data by the Country Code using the fewest possible steps. What should you do?

A. Set up a YouTube data source for your channel data for Data Studio. Set Views as the metric and set Video Title as a report dimension. Set Country Code as a filter.

B. Set up a YouTube data source for your channel data for Data Studio. Set Views as the metric and set Video Title and Country Code as report dimensions.

C. Export your YouTube views to Cloud Storage. Set up a Cloud Storage data source for Data Studio. Set Views as the metric and set Video Title as a report dimension. Set Country Code as a filter.

D. Export your YouTube views to Cloud Storage. Set up a Cloud Storage data source for Data Studio. Set Views as the metric and set Video Title and Country Code as report dimensions.

---

Feedback

B (Correct Answer) - B is correct because there is no need to export; you can use the existing YouTube data source. Country Code is a dimension because it's a string and should be displayed as such, that is, showing all countries, instead of filtering.

A is not correct because you cannot produce a summarized report that meets your business requirements using the options listed.

C and D are not correct because you do not need to export data from YouTube to Cloud Storage; you can simply use the existing YouTube data source.

---

##### You created a job which runs daily to import highly sensitive data from an on-premises location to Cloud Storage. You also set up a streaming data insert into Cloud Storage via a Kafka node that is running on a Compute Engine instance. You need to encrypt the data at rest and supply your own encryption key. Your key should not be stored in the Google Cloud. What should you do?

A. Create a dedicated service account, and use encryption at rest to reference your data stored in Cloud Storage and Compute Engine data as part of your API service calls.

B. Upload your own encryption key to Cloud Key Management Service, and use it to encrypt your data in Cloud Storage. Use your uploaded encryption key and reference it as part of your API service calls to encrypt your data in the Kafka node hosted on Compute Engine.

C. Upload your own encryption key to Cloud Key Management Service, and use it to encrypt your data in your Kafka node hosted on Compute Engine.

D. Supply your own encryption key, and reference it as part of your API service calls to encrypt your data in Cloud Storage and your Kafka node hosted on Compute Engine.

---

Feedback

D (Correct Answer) - D is correct because the scenario requires you to use your own key and also to not store your key on Compute Engine, and also this is a Google recommended practice; see the links below.

A is not correct because the scenario states that you must supply your own encryption key instead of using one generated by Google Cloud Platform.

B is not correct because the scenario states that you should use, but not store, your own key with Google Cloud Platform services.

C is not correct because it does not meet the scenario requirement to reference, but not store, your own key with Google Cloud Platform services.

---

##### You are working on a project with two compliance requirements. The first requirement states that your developers should be able to see the Google Cloud Platform billing charges for only their own projects. The second requirement states that your finance team members can set budgets and view the current charges for all projects in the organization. The finance team should not be able to view the project contents. You want to set permissions. What should you do?

A. Add the finance team members to the default IAM Owner role. Add the developers to a custom role that allows them to see their own spend only.

B. Add the finance team members to the Billing Administrator role for each of the billing accounts that they need to manage. Add the developers to the Viewer role for the Project.

C. Add the developers and finance managers to the Viewer role for the Project.

D. Add the finance team to the Viewer role for the Project. Add the developers to the Security Reviewer role for each of the billing accounts.

---

Feedback

B (Correct Answer) - B is correct because it uses the principle of least privilege for IAM roles; use the Billing Administrator IAM role for that job function.

A, C, and D are not correct because is it a Google best practice to use pre-defined IAM roles when they exist and match your business scenario; see the link below.

---
##### You are working on optimizing BigQuery for a query that is run repeatedly on a single table. The data queried is about 1 GB, and some rows are expected to change about 10 times every hour. You have optimized the SQL statements as much as possible. You want to further optimize the query's performance. What should you do?

A. Create a materialized view based on the table, and query that view.
B. Enable caching of the queried data so that subsequent queries are faster.
C. Create a scheduled query, and run it a few minutes before the report has to be created.
D. Reserve a larger number of slots in advance so that you have maximum compute power to execute the query.

---
Feedback

A (correct): Option A is correct because materialized views periodically cache the results of a query for increased performance. Materialized views are suited to small datasets that are frequently queried. When underlying table data changes, the materialized view invalidates the affected portions and re-reads them.

B: Option B is not correct because caching is automatically enabled but is not performant when the underlying data changes.

C: Option C is not correct because scheduled queries let you schedule recurring queries but do not provide specific performance
optimizations. Also, running a query too early could use old/stale data.

D: Option D is not correct because reserving more slots guarantees the availability of BigQuery slots but does not improve performance.

##### Several years ago, you built a machine learning model for an ecommerce company. Your model made good predictions. Then a global pandemic occurred, lockdowns were imposed, and many people started working from home. Now the quality of your model has degraded. You want to improve the quality of your model and prevent future performance degradation. What should you do?

A. Retrain the model with data from the first 30 days of the lockdown.

B. Monitor data until usage patterns normalize, and then retrain the model.

C. Retrain the model with data from the last 30 days. After one year, return to the older model.

D. Retrain the model with data from the last 30 days. Add a step to continuously monitor model input data for changes, and retrain the model.
 
Feedback
A: Option A is not correct because retraining based on the data from the first 30 days of the lockdown might only be useful for predictions during similar lockdowns and not for regular periods.

B: Option B is not correct because usage patterns might have changed permanently and might continue to change in the future.

C: Option C is not correct because the older model might not be indicative of user behavior after a year.

D(correct): Option D is correct because the data used to build the original model is no longer relevant. Retraining the model with recent data from the last 30 days will improve the predictions. To keep a watch on future data drifts, monitor the incoming data.

##### A new member of your development team works remotely. The developer will write code locally on their laptop, which will connect to a MySQL instance on Cloud SQL. The instance has an external (public) IP address. You want to follow Google-recommended practices when you give access to Cloud SQL to the new team member. What should you do?
A. Ask the developer for their laptop's IP address, and add it to the authorized networks list.

B. Remove the external IP address, and replace it with an internal IP address. Add only the IP address for the remote developer's laptop to the authorized list.

C. Give instance access permissions in Identity and Access Management (IAM), and have the developer run Cloud SQL Auth proxy to connect to a MySQL instance.

D. Give instance access permissions in Identity and Access Management (IAM), change the access to "private service access" for security, and allow the developer to access Cloud SQL from their laptop.
 
Feedback
A: Option A is not correct, because although adding an authorized networks list is possible, it is more effort to track it and also less secure.
B: Option B is not correct, because if you remove the external IP address, access for those who work remotely will be more complicated because they also have to be within private RFC 1918 address space.
C(correct): Option C is correct because the recommended approach is to use Cloud SQL Auth proxy. Permissions can be controlled by IAM. You don't need to track authorization lists for changing user IP addresses.
D: Option D is not correct because private service access will require access from a private RFC 1918 address space, which might not be available to developers who work remotely.

##### Your Cloud Spanner database stores customer address information that is frequently accessed by the marketing team. When a customer enters the country and the state where they live, this information is stored in different tables connected by a foreign key. The current architecture has performance issues. You want to follow Google-recommended practices to improve performance. What should you do?

A. Create interleaved tables, and store states under the countries.

B. Denormalize the data, and have a row for each state with its corresponding country.

C. Retain the existing architecture, but use short, two-letter codes for the countries and states.

D. Combine the countries in a single cell's text, for example "country:state1,state2, …" and when required, split the data.

Feedback
A(correct): Option A is correct because Cloud Spanner supports interleaving that guarantees data being stored in the same split, which is performant when you need a strong data locality relationship.
B: Option B is not correct because denormalizing is not a preferred approach in relational databases. It leads to multiple rows with repeated data.
C: Option C is not correct because reducing the size of the fields to short names will have lower impact because the data access and joins will be a bigger performance issue.
D: Option D is not correct because packing multiple types of data into the same cell is not recommended for relational databases.

##### Your company runs its business-critical system on PostgreSQL. The system is accessed simultaneously from many locations around the world and supports millions of customers. Your database administration team manages the redundancy and scaling manually. You want to migrate the database to Google Cloud. You need a solution that will provide global scale and availability and require minimal maintenance. What should you do?

A. Migrate to BigQuery.

B. Migrate to Cloud Spanner.

C. Migrate to a Cloud SQL for PostgreSQL instance.

D. Migrate to bare metal machines with PostgreSQL installed.

Feedback
A: Option A is not correct because BigQuery doesn’t support global scale. BigQuery also isn’t the best option for migrating a transactional database like PostgreSQL because it is more analytics-focused.
B(correct): Option B is correct because Cloud Spanner provides a global-scale, highly available database that supports relational data.
C: Option C is not correct because Cloud SQL options are regional and have less scalability compared to Cloud Spanner.
D: Option D is not correct because running PostgreSQL on bare metal machines requires a greater maintenance effort.

##### Your company collects data about customers to regularly check their health vitals. You have millions of customers around the world. Data is ingested at an average rate of two events per 10 seconds per user. You need to be able to visualize data in Bigtable on a per user basis. You need to construct the Bigtable key so that the operations are performant. What should you do?
A(correct). Construct the key as user-id#device-id#activity-id#timestamp.

B. Construct the key as timestamp#user-id#device-id#activity-id.

C. Construct the key as timestamp#device-id#activity-id#user-id.

D. Construct the key as user-id#timestamp#device-id#activity-id.

Feedback
A(correct): Option A is correct because the design does not monotonically increase, thus avoiding hotspots.

B: Option B is not correct because it monotonically increases, thus causing hotspots.

C: Option C is not correct because it monotonically increases, thus causing hotspots.

D: Option D is not correct because it monotonically increases, thus causing hotspots.


##### Your company is hiring several business analysts who are new to BigQuery. The analysts will use BigQuery to analyze large quantities of data. You need to control costs in BigQuery and ensure that there is no budget overrun while you maintain  the quality of query results. What should you do?

A(correct). Set a customized project-level or user-level daily quota to acceptable values.
 
B. Reduce the data in the BigQuery table so that the analysts query less data, and then archive the remaining data.

C. Train the analysts to use the query validator or --dry_run to estimate costs so that the analysts can self-regulate usage.

D. Export the BigQuery daily costs, and visualize the data on Looker on a per-analyst basis so that the analysts can self-regulate usage.

Feedback
A(correct): Option A is correct because if you have multiple BigQuery projects and users, you can manage costs by requesting a custom quota that specifies a limit on the amount of query data processed per day.
B: Option B is not correct because giving only partial data to the analysts might not produce accurate query results.
C: Option C is not correct because costs could still overrun budgets. This approach assumes that analysts always follow guidelines.
D: Option D is not correct because your costs could still overrun budgets. This approach also assumes that the analysts look at the charts daily and adjust their behavior.

##### Your Bigtable database was recently deployed into production. The scale of data ingested and analyzed has increased significantly, but the performance has degraded. You want to identify the performance issue. What should you do?

A(correct). Use Key Visualizer to analyze performance.

B. Use Cloud Trace to identify the performance issue.

C. Add logging statements into the code to see which inserts cause the delay.

D. Add more nodes to the cluster to see if that resolves the performance issue.

Feedback
A(correct): Option A is correct because Key Visualizer for Bigtable generates visual reports for your tables that detail your usage based on the row keys that you access, show you how Bigtable operates, and can help you troubleshoot performance issues.
B: Option B is not correct because Cloud Trace is used to debug latency in applications.
C: Option C is not correct because adding logging statements won't help you understand the performance issues within Bigtable.
D: Option D is not correct because adding more nodes might improve the performance, but the database could continue to have performance issues if the keys are not designed well.

##### Your company is moving your data analytics to BigQuery. Your other operations will remain on-premises. You need to transfer 800 TB of historic data. You also need to plan for 30 Gbps of daily data transfers that must be appended for analysis the next day. You want to follow Google-recommended practices to transfer your data. What should you do?

A. As early as possible every day, use Cloud VPN to transfer the existing data over the internet.

B. Use a Transfer Appliance to move the existing data to Google Cloud. Use Cloud VPN to transfer data daily.

C. Use a Transfer Appliance to move the existing data to Google Cloud.. Use VPC Network Peering to transfer data daily.

D. Use a Transfer Appliance to move the existing data to Google Cloud. Set up a Dedicated or Partner Interconnect for daily transfers.
 
Feedback
A: Option A is not correct because the internet in general will have less stability and much lower speed. Transferring large amounts of data is not viable.
B: Option B is not correct because Cloud VPN is useful for data transfers at a rate of a few Gbps (1.5 Gbps to 3 Gbps).
C: Option C is not correct because VPC Network Peering is used for data transfers within Google Cloud Organizations.
D(correct): Option D is correct because using a Transfer Appliance is recommended to transfer hundreds of terabytes of data. For large data transfers that occur regularly, a dedicated, hybrid networking connection is recommended.

##### Your team runs Dataproc workloads where the worker node takes about 45 minutes to process. You have been exploring various options to optimize the system for cost, including shutting down worker nodes aggressively. However, in your metrics you see that the entire job takes even longer. You want to optimize the system for cost without increasing job completion time. What should you do?

A. Set a graceful decommissioning timeout greater than 45 minutes.

B. Rewrite the processing in Cloud Data Fusion, and run the job automatically.

C. Rewrite the processing in Dataflow, and use stream processing of the same data.

D. Increase the number of vCPUs on each worker node so that the processing finishes sooner.

Correct answer
A. Set a graceful decommissioning timeout greater than 45 minutes.
Feedback
A(correct): Option A is correct because graceful decommissioning will finish work in progress on a worker node before it is removed from the Dataproc cluster.
B: Option B is not correct because rebuilding the data pipeline in Cloud Data Fusion will increase effort, cost, and time.
C: Option C is not correct because rewriting the code in Dataflow will increase effort, cost, and time.
D: Option D is not correct because increasing the number of vCPUs will greatly increase the cost.

##### Our customer has a SQL Server database that contains about 5 TB of data in another public cloud. You expect the data to grow to a maximum of 25 TB. The database is the backend of an internal reporting application that is used once a week. You want to migrate the application to Google Cloud to reduce administrative effort while keeping costs the same or reducing them. What should you do?

A. Migrate the database to Bigtable.

B. Migrate the database to Cloud Spanner.

C. Install SQL Server on a Compute Engine VM.

D. Migrate the database to SQL Server in Cloud SQL.

Feedback
A: Option A is not correct because Bigtable is a NoSQL database and is not a suitable destination from a SQL Server source.
B: Option B is not correct because Cloud Spanner will be costlier than Cloud SQL. Although Spanner has global availability, it is unnecessary for this application requirement.
C: Option C is not correct because installing a custom SQL Server instance on a Compute Engine VM will require more administrative effort.
D(correct): Option D is correct because Cloud SQL provides managed MySQL, PostgreSQL, and SQL Server databases, which will reduce administrative effort. Twenty-five TB can be accommodated efficiently on Cloud SQL.

##### Your IT team uses BigQuery for storing structured data. Your finance team recently moved to Google Workspace Enterprise edition from a standalone, desktop-based spreadsheet processor. When the finance team needs data insights, the IT team runs a query on BigQuery, exports the data to a CSV file, and sends the file as an email attachment to the finance team members. You want to improve the process while you retain familiar methods of data analysis for the finance team. What should you do?

A. Run the query in BigQuery, and give the finance team access to the results view, which can be analyzed.

B. Run the query in BigQuery, and give the finance team access to the data visualizations in Google Data Studio.

C. Run the query in BigQuery, export the data to CSV, upload the file to a Cloud Storage bucket, and share the file with the finance team.

D(correct). Run the query in BigQuery, and save the results to a Google Sheets shared spreadsheet that can be accessed and analyzed by the finance team.
 
Feedback
A: Option A is not correct because the finance team will have to be given Google Cloud access and be trained on using BigQuery, which is not a familiar method.
B: Option B is not correct because only giving the visualizations on Data Studio won't let the finance teams analyze the data.
C: Option C is not correct because the finance team will have to be given Google Cloud access and be trained on using Cloud Storage, which is not a familiar method.
D(correct): Option D is correct because Connected Sheets gives you a direct and easy way to share BigQuery data through Google Sheets.

# Your scooter-sharing company collects information about their scooters, such as location, battery level, and speed. The company visualizes this data in real time. To guard against intermittent connectivity, each scooter sends repeats of certain messages within a short interval. Occasional data errors have been noticed. The messages are received in Pub/Sub and stored in BigQuery. You need to ensure that the data does not contain duplicates and that erroneous data with empty fields is rejected. What should you do?

A. Store the data in BigQuery, and run delete queries on erroneous and duplicate data.

B(correct). Use Dataflow to subscribe to Pub/Sub, process the data, and store the data in BigQuery.

C. Use Kubernetes to create a microservices application that can remove duplicates and erroneous data. Then insert the data into BigQuery.

D. Create an application on Compute Engine with Managed Instance Groups that can remove duplicates and erroneous data. Then insert the data into BigQuery.

Feedback
A: Option A is not correct because directly storing data in BigQuery could cause data to be overwritten, and erroneous data could be present before it is deleted. Workarounds within BigQuery to circumvent these concerns would cost more effort, time, and money.
B(correct): Option B is correct because Dataflow is the recommended data processing product for streaming data. Dataflow can be programmed to remove duplicates, delete empty fields, and perform other custom data processing.
C: Option C is not correct because creating a custom application for streaming processing on Kubernetes is a significant effort and is not recommended.
D: Option D is not correct because creating a custom application for streaming processing on Compute Engine is a significant effort and is not recommended.

##### Your cryptocurrency trading company visualizes prices to help your customers make trading decisions. Because different trades happen in real time, the price data is fed to a data pipeline that uses Dataflow for processing. You want to compute moving averages. What should you do?

A. Use hopping windows in Dataflow.

B. Use session windows in Dataflow.

C. Use tumbling windows in Dataflow.

D. Use Dataflow SQL, and compute averages grouped by time.

Feedback
A(correct): Option A is correct because you use hopping windows to compute moving averages.
B: Option B is not correct because session windows are not used to calculate moving averages.
C: Option C is not correct because tumbling windows are not used to calculate moving averages.
D: Option D is not correct because grouping by time alone does not give you a moving average.

##### You are building the trading platform for a stock exchange with millions of traders. Trading data is written rapidly. You need to retrieve data quickly to show visualizations to the traders, such as the changing price of a particular stock over time. You need to choose a storage solution in Google Cloud. What should you do?

A. Use Bigtable.

B. Use Firestore.

C. Use Cloud SQL.

D. Use Memorystore.
 
Feedback
A(correct): Option A is correct because Bigtable is the recommended database for time series data that requires high throughput reads and writes.
B: Option B is not correct because Firestore does not have the high throughput capabilities that are suitable for time-series data.
C: Option C is not correct because Cloud SQL does not the have high throughput capabilities that are suitable for time-series data.
D: Option D is not correct because Memorystore is a fast in-memory database that is not suitable for persistently storing large amounts of data.

##### Your customer uses Hadoop and Spark to run data analytics on-premises. The main data is stored in hard disks that are centrally accessed. Your customer needs to migrate their workloads to Google Cloud efficiently while considering scalability. You want to select an architecture that requires minimal effort. What should you do?

A(correct). Use Dataproc to run Hadoop and Spark jobs. Move the data to Cloud Storage.

B. Use Dataflow to recreate the jobs in a serverless approach. Move the data to Cloud Storage.

C. Use Dataproc to run Hadoop and Spark jobs. Retain the data on a Compute Engine VM with an attached persistent disk.

D. Use Dataflow to recreate the jobs in a serverless approach. Retain the data on a Compute Engine VM with an attached persistent disk.

Feedback
A(correct): Option A is correct because Dataproc is a fully managed service for hosting open source distributed processing platforms, such as Apache Spark, Presto, Apache Flink and Apache Hadoop on Google Cloud. Cloud Storage is the preferred storage option for all persistent storage needs.
B: Option B is not correct because using Dataflow requires you to rewrite all the jobs.
C: Option C is not correct because storing the centrally accessed data on persistent disks is not recommended.
D: Option D is not correct because using Dataflow requires you to rewrite all the jobs. Storing the centrally accessed data on persistent disks is not recommended.

##### You used a small amount of data to build a machine learning model that gives you good inferences during testing. However, the results show more errors when real-world data is used to run the model. No additional data can be collected for testing. You want to get a more accurate view of the model's capability. What should you do?

A. Reduce the amount of data to improve the model.

B(correct). Cross-validate the data, and re-run the model building process.

C. Create feature crosses that will add new columns to increase the data.

D. Duplicate the data twice to increase the data, and re-run the model building process.

Feedback
A: Option A is not correct because this model is not underfitting.
B(correct): Option B is correct because this model appears to be overfitting. Using cross-validation will run the validation on multiple folds of the data, which reduces the overfitting.
C: Option C is not correct because adding new columns will not reduce the overfitting.
D: Option D is not correct because duplicating the data will not reduce the overfitting.

##### Your organization has been collecting information for many years about your customers, including their address and credit card details. You plan to use this customer data to build machine learning models on Google Cloud. You are concerned about private data leaking into the machine learning model. Your management is also concerned that direct leaks of personal data could damage the company's reputation. You need to address these concerns about data security. What should you do?

A. Remove all the tables that contain sensitive data.

B. Use libraries like SciPy to build the ML models on your local computer.

C. Remove the sensitive data by using the Cloud Data Loss Prevention (DLP) API.

D. Identify the rows that contain sensitive data, and apply SQL queries to remove only those rows.

Feedback
A: Option A is not correct because removing data, such as entire tables, could reduce the effectiveness of the resulting model.
B: Option B is not correct because building machine learning models on individual computers is not a viable approach when it involves large amounts of data.
C(correct): Option C is correct because Cloud DLP is the recommended approach to redact, mask, tokenize, and transform text and images to help protect data privacy.
D: Option D is not correct because removing data, such as full rows, could reduce the effectiveness of the resulting model.

##### Your healthcare application has a backend system that accepts event data directly from IoT devices. Recent increases of the application's users and devices are causing a sudden influx of data that overwhelms the system. You need to redesign the data pipeline to ensure that all data is processed and that no events are lost. You want to follow Google-recommended practices. What should you do?  

A. Use Kafka with pull mode.

B(correct). Use Pub/Sub with pull mode.

C. Use Pub/Sub with push mode.

D. Run Cloud Scheduler at fixed intervals.

Feedback
A: Option A is not correct because Kafka is not a managed solution in Google Cloud. The Google-recommended option is Pub/Sub, a fully managed, serverless solution.
B(correct): Option B is correct because pull mode allows new event data to be pulled for processing on demand when the previous data is processed. Pub/Sub will absorb and retain new events in the interim without losing them.
C: Option C is not correct because Pub/Sub in push mode could continue to overwhelm the system.
D: Option D is not correct because new event data should be pulled for processing when the previous processing is completed, and that is not expected to be at fixed intervals.

##### You work for a large fast food restaurant chain with over 400,000 employees. You store employee information in Google BigQuery in a Users table consisting of a FirstName field and a LastName field. A member of IT is building an application and asks you to modify the schema and data in BigQuery so the application can query a FullName field consisting of the value of the FirstName field concatenated with a space, followed by the value of the LastName field for each employee. How can you make that data available while minimizing cost?

A. Create a view in BigQuery that concatenates the FirstName and LastName field values to produce the FullName.

B(correct). Add a new column called FullName to the Users table. Run an UPDATE statement that updates the FullName column for each user with the concatenation of the FirstName and LastName values.

C. Create a Google Cloud Dataflow job that queries BigQuery for the entire Users table, concatenates the FirstName value and LastName value for each user, and loads the proper values for FirstName, LastName, and FullName into a new table in BigQuery.

D. Use BigQuery to export the data for the table to a CSV file. Create a Google Cloud Dataproc job to process the CSV file and output a new CSV file containing the proper values for FirstName, LastName and FullName. Run a BigQuery load job to load the new CSV file into BigQuery.

Feedback
Overall explanation
Correct: B BigQuery has no quota on the DML statements. (Search Google - does bigquery have quota for update). Why not C: This is a one time activity and SQL is the easiest way to program it. DataFlow is way overkill for this. You will need to find an engineer who can develop DataFlow pipelines. Whereas, SQL is so much more widely known and easier. One of the great features about BigQuery is its SQL interface. Even for BigQueryML services.

##### You have spent a few days loading data from comma-separated values (CSV) files into the Google BigQuery table CLICK_STREAM. The column DT stores the epoch time of click events. For convenience, you chose a simple schema where every field is treated as the STRING type. Now, you want to compute web session durations of users who visit your site, and you want to change its data type to the TIMESTAMP. You want to minimize the migration effort without making future queries computationally expensive. What should you do?

A. Delete the table CLICK_STREAM, and then re-create it such that the column DT is of the TIMESTAMP type. Reload the data.

B. Add a column TS of the TIMESTAMP type to the table CLICK_STREAM, and populate the numeric values from the column TS for each row. Reference the column TS instead of the column DT from now on.

C. Create a view CLICK_STREAM_V, where strings from the column DT are cast into TIMESTAMP values. Reference the view CLICK_STREAM_V instead of the table CLICK_STREAM from now on.

D. Add two columns to the table CLICK STREAM: TS of the TIMESTAMP type and IS_NEW of the BOOLEAN type. Reload all data in append mode. For each appended row, set the value of IS_NEW to true. For future queries, reference the column TS instead of the column DT, with the WHERE clause ensuring that the value of IS_NEW must be true.

E(correct). Construct a query to return every row of the table CLICK_STREAM, while using the built-in function to cast strings from the column DT into TIMESTAMP values. Run the query into a destination table NEW_CLICK_STREAM, in which the column TS is the TIMESTAMP type. Reference the table NEW_CLICK_STREAM instead of the table CLICK_STREAM from now on. In the future, new data is loaded into the table NEW_CLICK_STREAM.

Feedback
E : Export and load data into a new table You can also change a column's data type by exporting your table data to Cloud Storage, and then loading the data into a new table with a schema definition that specifies the correct data type for the column. You can also use the load job to overwrite the existing table. Advantages You are not charged for the export job or the load job. Currently, BigQuery load and export jobs are free. If you use the load job to overwrite the original table, you incur storage costs for one table instead of two, but you lose the original data. Disadvantages If you load the data into a new table, you incur storage costs for the original table and the new table (unless you delete the old one). You incur costs for storing the exported data in Cloud Storage.

##### You use a dataset in BigQuery for analysis. You want to provide third-party companies with access to the same dataset. You need to keep the costs of data sharing low and ensure that the data is current. Which solution should you choose?

A(correct) Create an authorized view on the BigQuery table to control data access, and provide third-party companies with access to that view.

B. Use Cloud Scheduler to export the data on a regular basis to Cloud Storage, and provide third-party companies with access to the bucket.

C. Create a separate dataset in BigQuery that contains the relevant data to share, and provide third-party companies with access to the new dataset.

D. Create a Cloud Dataflow job that reads the data in frequent time intervals, and writes it to the relevant BigQuery dataset or Cloud Storage bucket for third-party companies to use.

Feedback
https://cloud.google.com/bigquery/docs/share-access-views BigQuery is a petabyte-scale analytics data warehouse that you can use to run SQL queries over vast amounts of data in near realtime. Giving a view access to a dataset is also known as creating an authorized view in BigQuery’. An authorized view allows you to share query results with particular users and groups without giving them access to the underlying tables. You can also use the view's SQL query to restrict the columns (fields) the users are able to query. When you create the view, it must be created in a dataset separate from the source data queried by the view. Because you can assign access controls only at the dataset level, if the view is created in the same dataset as the source data, your data analysts would have access to both the view and the data.

##### You set up a streaming data insert into a Redis cluster via a Kafka cluster. Both clusters are running on Compute Engine instances. You need to encrypt data at rest with encryption keys that you can create, rotate, and destroy as needed. What should you do?

A. Create a dedicated service account, and use encryption at rest to reference your data stored in your Compute Engine cluster instances as part of your API service calls.
Your answer is correct

B(correct). Create encryption keys in Cloud Key Management Service. Use those keys to encrypt your data in all of the Compute Engine cluster instances.

C. Create encryption keys locally. Upload your encryption keys to Cloud Key Management Service. Use those keys to encrypt your data in all of the Compute Engine cluster instances.

D. Create encryption keys in Cloud Key Management Service. Reference those keys in your API service calls when accessing the data in your Compute Engine cluster instances.

Feedback
A makes no sense, you need to use your own keys. You don’t create keys locally and upload them, you should import it to make it work..using the kms public key…not just “uploading” it. C is also out. IT’s between B and D Cloud KMS is a cloud-hosted key management service that lets you manage cryptographic keys for your cloud services the same way you do on-premises, You can generate, use, rotate, and destroy cryptographic keys from there. Since you want to encrypt data at rest, is B, you don’t use them for any API calls. https://cloud.google.com/compute/docs/disks/customer-managed-encryption

##### You work for a manufacturing company that sources up to 750 different components, each from a different supplier. You've collected a labeled dataset that has on average 1000 examples for each unique component. Your team wants to implement an app to help warehouse workers recognize incoming components based on a photo of the component. You want to implement the first working version of this app (as Proof-Of-Concept) within a few working days. What should you do?

A(correct). Use Cloud Vision AutoML with the existing dataset.

B. Use Cloud Vision AutoML, but reduce your dataset twice.

C. Use Cloud Vision API by providing custom labels as recognition hints.

D. Train your own image recognition model leveraging transfer learning techniques.

##### You work for a car manufacturer and have set up a data pipeline using Google Cloud Pub/Sub to capture anomalous sensor events. You are using a push subscription in Cloud Pub/Sub that calls a custom HTTPS endpoint that you have created to take action of these anomalous events as they occur. Your customHTTPS endpoint keeps getting an inordinate amount of duplicate messages. What is the most likely cause of these duplicate messages?

A. The message body for the sensor event is too large.

B. Your custom endpoint has an out-of-date SSL certificate.

C. The Cloud Pub/Sub topic has too many messages published to it.

D(correct). Your custom endpoint is not acknowledging messages within the acknowledgement deadline.

##### Your infrastructure includes a set of YouTube channels. You have been tasked with creating a process for sending the YouTube channel data to Google Cloud for analysis. You want to design a solution that allows your world-wide marketing teams to perform ANSI SQL and other types of analysis on up-to-date YouTube channels log data. How should you set up the log data transfer into Google Cloud?

A(correct). Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Multi-Regional storage bucket as a final destination.

B. Use Storage Transfer Service to transfer the offsite backup files to a Cloud Storage Regional bucket as a final destination.

C. Use BigQuery Data Transfer Service to transfer the offsite backup files to a Cloud Storage Multi-Regional storage bucket as a final destination.

D. Use BigQuery Data Transfer Service to transfer the offsite backup files to a Cloud Storage Regional storage bucket as a final destination.

Feedback
Correct Answer: A Destination is GCS and having multi-regional so A is the best option available. Even since BigQuery Data Transfer Service initially supports Google application sources like Google Ads, Campaign Manager, Google Ad Manager and YouTube but it does not support destination anything other than bq data set

##### You work for a bank. You have a labelled dataset that contains information on already granted loan application and whether these applications have been defaulted. You have been asked to train a model to predict default rates for credit applicants.What should you do?

A. Increase the size of the dataset by collecting additional data.

B. Train a linear regression to predict a credit default risk score.
Your answer is incorrect

C. Remove the bias from the data and collect applications that have been declined loans.
Correct answer

D(correct). Match loan applicants with their social profiles to enable feature engineering.

Feedback
D. A - Incorrect. There's no indication that size was the problem. B - Incorrect. The model is likely to be a classification model. So linear is not the best fit. C - Incorrect. You wouldn't need declined applications. How can you default without getting an approved application. It's not relevant.

##### You have a query that filters a BigQuery table using a WHERE clause on timestamp and ID columns. By using bq query "" -dry_run you learn that the query triggers a full scan of the table, even though the filter on timestamp and ID select a tiny fraction of the overall data. You want to reduce the amount of data scanned by BigQuery with minimal changes to existing SQL queries. What should you do?

A. Create a separate table for each ID.

B. Use the LIMIT keyword to reduce the number of rows returned.
Your answer is correct

C(correct). Recreate the table with a partitioning column and clustering column.

D. Use the bq query - -maximum_bytes_billed flag to restrict the number of bytes billed.

Feedback
https://cloud.google.com/bigquery/docs/best-practices-costs

##### Flowlogistic Case Study - Company Overview - Flowlogistic is a leading logistics and supply chain provider. They help businesses throughout the world manage their resources and transport them to their final destination. The company has grown rapidly, expanding their offerings to include rail, truck, aircraft, and oceanic shipping. Company Background - The company started as a regional trucking company, and then expanded into other logistics market. Because they have not updated their infrastructure, managing and tracking orders and shipments has become a bottleneck. To improve operations, Flowlogistic developed proprietary technology for tracking shipments in real time at the parcel level. However, they are unable to deploy it because their technology stack, based on Apache Kafka, cannot support the processing volume. In addition, Flowlogistic wants to further analyze their orders and shipments to determine how best to deploy their resources. Solution Concept - Flowlogistic wants to implement two concepts using the cloud: ✑ Use their proprietary technology in a real-time inventory-tracking system that indicates the location of their loads ✑ Perform analytics on all their orders and shipment logs, which contain both structured and unstructured data, to determine how best to deploy resources, which markets to expand info. They also want to use predictive analytics to learn earlier when a shipment will be delayed. Existing Technical Environment - Flowlogistic architecture resides in a single data center: ✑ Databases 8 physical servers in 2 clusters - SQL Server "" user data, inventory, static data 3 physical servers - Cassandra "" metadata, tracking messages 10 Kafka servers "" tracking message aggregation and batch insert ✑ Application servers "" customer front end, middleware for order/customs 60 virtual machines across 20 physical servers - Tomcat "" Java services - Nginx "" static content - Batch servers ✑ Storage appliances - iSCSI for virtual machine (VM) hosts - Fibre Channel storage area network (FC SAN) "" SQL server storage - Network-attached storage (NAS) image storage, logs, backups ✑ 10 Apache Hadoop /Spark servers - Core Data Lake - Data analysis workloads ✑ 20 miscellaneous servers - Jenkins, monitoring, bastion hosts, Business Requirements - ✑ Build a reliable and reproducible environment with scaled panty of production. ✑ Aggregate data in a centralized Data Lake for analysis ✑ Use historical data to perform predictive analytics on future shipments ✑ Accurately track every shipment worldwide using proprietary technology ✑ Improve business agility and speed of innovation through rapid provisioning of new resources ✑ Analyze and optimize architecture for performance in the cloud Migrate fully to the cloud if all other requirements are met Technical Requirements - ✑ Handle both streaming and batch data ✑ Migrate existing Hadoop workloads ✑ Ensure architecture is scalable and elastic to meet the changing demands of the company. ✑ Use managed services whenever possible ✑ Encrypt data flight and at rest ✑ Connect a VPN between the production data center and cloud environment SEO Statement - We have grown so quickly that our inability to upgrade our infrastructure is really hampering further growth and efficiency. We are efficient at moving shipments around the world, but we are inefficient at moving data around. We need to organize our information so we can more easily understand where our customers are and what they are shipping. CTO Statement - IT has never been a priority for us, so as our data has grown, we have not invested enough in our technology. I have a good staff to manage IT, but they are so busy managing our infrastructure that I cannot get them to do the things that really matter, such as organizing our data, building the analytics, and figuring out how to implement the CFO' s tracking technology. CFO Statement - Part of our competitive advantage is that we penalize ourselves for late shipments and deliveries. Knowing where out shipments are at all times has a direct correlation to our bottom line and profitability. Additionally, I don't want to commit capital to building out a server environment. Flowlogistic's management has determined that the current Apache Kafka servers cannot handle the data volume for their real-time inventory tracking system. You need to build a new system on Google Cloud Platform (GCP) that will feed the proprietary tracking software. The system must be able to ingest data from a variety of global sources, process and query in real-time, and store the data reliably. Which combination of GCP products should you choose?


A(correct). Cloud Pub/Sub, Cloud Dataflow, and Cloud Storage

B. Cloud Pub/Sub, Cloud Dataflow, and Local SSD

C. Cloud Pub/Sub, Cloud SQL, and Cloud Storage

D. Cloud Load Balancing, Cloud Dataflow, and Cloud Storage

##### Your company needs to upload their historic data to Cloud Storage. The security rules don't allow access from external IPs to their on-premises resources. After an initial upload, they will add new data from existing on-premises applications every day. What should they do?

A(correct). Execute gsutil rsync from the on-premises servers.

B. Use Cloud Dataflow and write the data to Cloud Storage.

C. Write a job template in Cloud Dataproc to perform the data transfer.

D. Install an FTP server on a Compute Engine VM to receive the files and move them to Cloud Storage.

Feedback
A is the better and most simple IF there is no problem in having gsutil in our servers. B and C no way, the comms will go GCP–Home, which sais is not allowed. D is valid, we can send the files with http://ftp…BUT ftp is not secure, and we’ll need to move them to the cloud storage afterwards, which is not detailed in the answer. https://cloud.google.com/storage/docs/gsutil/commands/rsync

##### You are implementing security best practices on your data pipeline. Currently, you are manually executing jobs as the Project Owner. You want to automate these jobs by taking nightly batch files containing non-public information from Google Cloud Storage, processing them with a Spark Scala job on a Google CloudDataproc cluster, and depositing the results into Google BigQuery.How should you securely run this workload?

A. Restrict the Google Cloud Storage bucket so only you can see the files

B. Grant the Project Owner role to a service account, and run the job with it

C(correct). Use a service account with the ability to read the batch files and to write to BigQuery

D. Use a user account with the Project Viewer role on the Cloud Dataproc cluster to read the batch files and write to BigQuery

Feedback
Data owners cant create jobs or queries. -> B out We need service Account -> D out Access only granting me does not solve the problem -> A out The answer is C. ( Minimum rights to perform the job)

##### Which of the following are feature engineering techniques? (Select 2 answers)
A. Hidden feature layers

B. Feature prioritization

C(correct). Crossed feature columns

D(correct). Bucketization of a continuous feature

Feedback
Selecting and crafting the right set of feature columns is key to learning an effective model. Bucketization is a process of dividing the entire range of a continuous feature into a set of consecutive bins/buckets, and then converting the original numerical feature into a bucket ID (as a categorical feature) depending on which bucket that value falls into. Using each base feature column separately may not be enough to explain the data. To learn the differences between different feature combinations, we can add crossed feature columns to the model. 
Reference: https://www.tensorflow.org/tutorials/wide#selecting_and_engineering_features_for_the_model

##### You are designing a cloud-native historical data processing system to meet the following conditions:✑ The data being analyzed is in CSV, Avro, and PDF formats and will be accessed by multiple analysis tools including Cloud Dataproc, BigQuery, and ComputeEngine.✑ A streaming data pipeline stores new data daily.✑ Peformance is not a factor in the solution.✑ The solution design should maximize availability.How should you design data storage for this solution?

A. Create a Cloud Dataproc cluster with high availability. Store the data in HDFS, and peform analysis as needed.

B. Store the data in BigQuery. Access the data using the BigQuery Connector on Cloud Dataproc and Compute Engine.

C. Store the data in a regional Cloud Storage bucket. Access the bucket directly using Cloud Dataproc, BigQuery, and Compute Engine.

D(correct). Store the data in a multi-regional Cloud Storage bucket. Access the data directly using Cloud Dataproc, BigQuery, and Compute Engine.

##### You are implementing several batch jobs that must be executed on a schedule. These jobs have many interdependent steps that must be executed in a specific order. Portions of the jobs involve executing shell scripts, running Hadoop jobs, and running queries in BigQuery. The jobs are expected to run for many minutes up to several hours. If the steps fail, they must be retried a fixed number of times. Which service should you use to manage the execution of these jobs?
A. Cloud Scheduler

B. Cloud Dataflow

C. Cloud Functions

D(correct). Cloud Composer

Feedback
D: the main point is that Cloud Composer should be used when there is inter-dependencies between the job, e.g. we need the output of a job to start another whenever the first finished, and use dependencies coming from first job.

##### You are managing a Cloud Dataproc cluster. You need to make a job run faster while minimizing costs, without losing work in progress on your clusters. What should you do?
A. Increase the cluster size with more non-preemptible workers.

B. Increase the cluster size with preemptible worker nodes, and configure them to forcefully decommission.

C. Increase the cluster size with preemptible worker nodes, and use Cloud Stackdriver to trigger a script to preserve work.

D(correct). Increase the cluster size with preemptible worker nodes, and configure them to use graceful decommissioning.

Feedback
D After creating a Dataproc cluster, you can adjust ("scale") the cluster by increasing or decreasing the number of primary or secondary worker nodes in the cluster. You can scale a Dataproc cluster at any time, even when jobs are running on the cluster. Use Dataproc Autoscaling. Instead of manually scaling clusters, enable Autoscaling to have Dataproc set the "right" number of workers for your workloads. Why scale a Dataproc cluster? to increase the number of workers to make a job run faster to decrease the number of workers to save money (see Graceful Decommissioning as an option to use when downsizing a cluster to avoid losing work in progress). to increase the number of nodes to expand available Hadoop Distributed Filesystem (HDFS) storage

##### You work for a manufacturing plant that batches application log files together into a single log file once a day at 2:00 AM. You have written a Google CloudDataflow job to process that log file. You need to make sure the log file in processed once per day as inexpensively as possible. What should you do?

A. Change the processing job to use Google Cloud Dataproc instead.

B. Manually start the Cloud Dataflow job each morning when you get into the office.

C(correct). Create a cron job with Google App Engine Cron Service to run the Cloud Dataflow job.
Your answer is incorrect

D. Configure the Cloud Dataflow job as a streaming job so that it processes the log data immediately.

Feedback
Answer is C. https://cloud.google.com/appengine/docs/flexible/nodejs/scheduling-jobs-with-cron-yaml


##### You have enabled the free integration between Firebase Analytics and Google BigQuery. Firebase now automatically creates a new table daily in BigQuery in the format app_events_YYYYMMDD. You want to query all of the tables for the past 30 days in legacy SQL. What should you do?

A(correct). Use the TABLE_DATE_RANGE function

B. Use the WHERE_PARTITIONTIME pseudo column

C. Use WHERE date BETWEEN YYYY-MM-DD AND YYYY-MM-DD

D. Use SELECT IF.(date >= YYYY-MM-DD AND date <= YYYY-MM-DD)

Feedback
https://cloud.google.com/blog/products/gcp/using-bigquery-and-firebase-analytics-to-understand-your-mobile-app?hl=am

##### A data scientist has created a BigQuery ML model and asks you to create an ML pipeline to serve predictions. You have a REST API application with the requirement to serve predictions for an individual user ID with latency under 100 milliseconds. You use the following query to generate predictions: SELECT predicted_label, user_id FROM ML.PREDICT (MODEL "˜dataset.model', table user_features). How should you create the ML pipeline?

A. Add a WHERE clause to the query, and grant the BigQuery Data Viewer role to the application service account.

B. Create an Authorized View with the provided query. Share the dataset that contains the view with the application service account.

C. Create a Cloud Dataflow pipeline using BigQueryIO to read results from the query. Grant the Dataflow Worker role to the application service account.

D(correct). Create a Cloud Dataflow pipeline using BigQueryIO to read predictions for all users from the query. Write the results to Cloud Bigtable using BigtableIO. Grant the Bigtable Reader role to the application service account so that the application can read predictions for individual users from Cloud Bigtable.

##### MJTelco Case Study -Company Overview -MJTelco is a startup that plans to build networks in rapidly growing, underserved markets around the world. The company has patents for innovative optical communications hardware. Based on these patents, they can create many reliable, high-speed backbone links with inexpensive hardware.Company Background -Founded by experienced telecom executives, MJTelco uses technologies originally developed to overcome communications challenges in space. Fundamental to their operation, they need to create a distributed data infrastructure that drives real-time analysis and incorporates machine learning to continuously optimize their topologies. Because their hardware is inexpensive, they plan to overdeploy the network allowing them to account for the impact of dynamic regional politics on location availability and cost.Their management and operations teams are situated all around the globe creating many-to-many relationship between data consumers and provides in their system. After careful consideration, they decided public cloud is the perfect environment to support their needs.Solution Concept -MJTelco is running a successful proof-of-concept (PoC) project in its labs. They have two primary needs:✑ Scale and harden their PoC to support significantly more data flows generated when they ramp to more than 50,000 installations.✑ Refine their machine-learning cycles to verify and improve the dynamic models they use to control topology definition.MJTelco will also use three separate operating environments "" development/test, staging, and production "" to meet the needs of running experiments, deploying new features, and serving production customers.Business Requirements -✑ Scale up their production environment with minimal cost, instantiating resources when and where needed in an unpredictable, distributed telecom user community.✑ Ensure security of their proprietary data to protect their leading-edge machine learning and analysis.✑ Provide reliable and timely access to data for analysis from distributed research workers✑ Maintain isolated environments that support rapid iteration of their machine-learning models without affecting their customers.Technical Requirements -✑ Ensure secure and efficient transport and storage of telemetry data✑ Rapidly scale instances to support between 10,000 and 100,000 data providers with multiple flows each.✑ Allow analysis and presentation against data tables tracking up to 2 years of data storing approximately 100m records/day✑ Support rapid iteration of monitoring infrastructure focused on awareness of data pipeline problems both in telemetry flows and in production learning cycles.CEO Statement -Our business model relies on our patents, analytics and dynamic machine learning. Our inexpensive hardware is organized to be highly reliable, which gives us cost advantages. We need to quickly stabilize our large distributed data pipelines to meet our reliability and capacity commitments.CTO Statement -Our public cloud services must operate as advertised. We need resources that scale and keep our data secure. We also need environments in which our data scientists can carefully study and quickly adapt our models. Because we rely on automation to process our data, we also need our development and test environments to work as we iterate.CFO Statement -The project is too large for us to maintain the hardware and software required for the data and analysis. Also, we cannot afford to staff an operations team to monitor so many data feeds, so we will rely on automation and infrastructure. Google Cloud's machine learning will allow our quantitative researchers to work on our high-value problems instead of problems with our data pipelines.MJTelco needs you to create a schema in Google Bigtable that will allow for the historical analysis of the last 2 years of records. Each record that comes in is sent every 15 minutes, and contains a unique identifier of the device and a data record. The most common query is for all the data for a given device for a given day.Which schema should you use?
A. Rowkey: date#device_id Column data: data_point

B. Rowkey: date Column data: device_id, data_point

C(correct). Rowkey: device_id Column data: date, data_point

D. Rowkey: data_point Column data: device_id, date

E. Rowkey: date#data_point Column data: device_id

##### Each analytics team in your organization is running BigQuery jobs in their own projects. You want to enable each team to monitor slot usage within their projects.What should you do?
A. Create a Stackdriver Monitoring dashboard based on the BigQuery metric query/scanned_bytes

B(correct). Create a Stackdriver Monitoring dashboard based on the BigQuery metric slots/allocated_for_project

C. Create a log export for each project, capture the BigQuery job execution logs, create a custom metric based on the totalSlotMs, and create a Stackdriver Monitoring dashboard based on the custom metric

D. Create an aggregated log export at the organization level, capture the BigQuery job execution logs, create a custom metric based on the totalSlotMs, and create a Stackdriver Monitoring dashboard based on the custom metric

Feedback
Vote for B A - Eliminated (it will not tell, anything about slots, it will show, which query scan how many data) B - Correct METRIC given slots/allocated_for_project GA (which is used to tell Slots used by project) Number of BigQuery slots currently allocated for query jobs in the project. https://cloud.google.com/monitoring/api/metrics_gcp C - No need for custom metric, we have already pre-defined metric for the given requirement. D - Eliminated (we need slots usage per project, not organization level)

##### You launched a new gaming app almost three years ago. You have been uploading log files from the previous day to a separate Google BigQuery table with the table name format LOGS_yyyymmdd. You have been using table wildcard functions to generate daily and monthly reports for all time ranges. Recently, you discovered that some queries that cover long date ranges are exceeding the limit of 1,000 tables and failing. How can you resolve this issue?
A. Convert all daily log tables into date-partitioned tables

B(correct). Convert the sharded tables into a single partitioned table

C. Enable query caching so you can cache data from previous months

D. Create separate views to cover each month, and query from these views

Feedback
https://cloud.google.com/bigquery/docs/creating-partitioned-tables#converting_date-sharded_tables_into_ingestion-time_partitioned_tables

##### You currently have a single on-premises Kafka cluster in a data center in the us-east region that is responsible for ingesting messages from IoT devices globally.Because large parts of globe have poor internet connectivity, messages sometimes batch at the edge, come in all at once, and cause a spike in load on yourKafka cluster. This is becoming difficult to manage and prohibitively expensive. What is the Google-recommended cloud native architecture for this scenario?
A. Edge TPUs as sensor devices for storing and transmitting the messages.
Your answer is incorrect

B. Cloud Dataflow connected to the Kafka cluster to scale the processing of incoming messages.
Correct answer

C(correct). An IoT gateway connected to Cloud Pub/Sub, with Cloud Dataflow to read and process the messages from Cloud Pub/Sub.

D. A Kafka cluster virtualized on Compute Engine in us-east with Cloud Load Balancing to connect to the devices around the world.

##### You operate a logistics company, and you want to improve event delivery reliability for vehicle-based sensors. You operate small data centers around the world to capture these events, but leased lines that provide connectivity from your event collection infrastructure to your event processing infrastructure are unreliable, with unpredictable latency. You want to address this issue in the most cost-effective way. What should you do?
A. Deploy small Kafka clusters in your data centers to buffer events.

B. Have the data acquisition devices publish data to Cloud Pub/Sub.

C(correct). Establish a Cloud Interconnect between all remote data centers and Google.

D. Write a Cloud Dataflow pipeline that aggregates all data in session windows.

Feedback
C. This is a tricky one. The issue here is the unreliable connection between data collection and data processing infrastructure, and to resolve it in a cost-effective manner. However, it also mentions that the company is using leased lines. I think replacing the leased lines with Cloud InterConnect would solve the problem, and hopefully not be an added expense. https://cloud.google.com/interconnect/docs/concepts/overview

##### You work for an advertising company, and you've developed a Spark ML model to predict click-through rates at advertisement blocks. You've been developing everything at your on-premises data center, and now your company is migrating to Google Cloud. Your data center will be closing soon, so a rapid lift-and-shift migration is necessary. However, the data you've been using will be migrated to migrated to BigQuery. You periodically retrain your Spark ML models, so you need to migrate existing training pipelines to Google Cloud. What should you do?
A. Use Cloud ML Engine for training existing Spark ML models

B. Rewrite your models on TensorFlow, and start using Cloud ML Engine

C(correct). Use Cloud Dataproc for training existing Spark ML models, but start reading data directly from BigQuery

D. Spin up a Spark cluster on Compute Engine, and train Spark ML models on the data exported from BigQuery

Overall explanation
Right option is C. https://cloud.google.com/dataproc/docs/tutorials/bigquery-sparkml

##### You are creating a model to predict housing prices. Due to budget constraints, you must run it on a single resource-constrained virtual machine. Which learning algorithm should you use?
A(correct). Linear regression

B. Logistic classification

C. Recurrent neural network

D. Feedforward neural network

Overall explanation
correct answer -> Linear Regression Linear regression is a statistical method that allows to summarize and study relationships between two continuous (quantitative) variables: One variable, denoted X, is regarded as the independent variable. The other variable denoted y is regarded as the dependent variable. Linear regression uses one independent variable X to explain or predict the outcome of the dependent variable y. Whenever you are told to predict some future value of a process which is currently running, you can go with a regression algorithm. Refeerence: https://towardsdatascience.com/do-you-know-how-to-choose-the-right-machine-learning-algorithm-among-7-different-types-295d0b0c7f60

##### Which of these statements about exporting data from BigQuery is false?
A. To export more than 1 GB of data, you need to put a wildcard in the destination filename.

B. The only supported export destination is Google Cloud Storage.

C(correct). Data can only be exported in JSON or Avro format.

D. The only compression option available is GZIP.

Overall explanation
Correct: C When you export data from BigQuery, note the following: You cannot export table data to a local file, to Google Sheets, or to Google Drive. The only supported export location is Cloud Storage. For information on saving query results, see Downloading and saving query results. You can export up to 1 GB of table data to a single file. If you are exporting more than 1 GB of data, use a wildcard to export the data into multiple files. When you export data to multiple files, the size of the files will vary. You cannot export nested and repeated data in CSV format. Nested and repeated data is supported for Avro and JSON exports. When you export data in JSON format, INT64 (integer) data types are encoded as JSON strings to preserve 64-bit precision when the data is read by other systems. You cannot export data from multiple tables in a single export job. You cannot choose a compression type other than GZIP when you export data using the Cloud Console or the classic BigQuery web UI.

##### You are deploying 10,000 new Internet of Things devices to collect temperature data in your warehouses globally. You need to process, store and analyze these very large datasets in real time. What should you do?
A. Send the data to Google Cloud Datastore and then export to BigQuery.

B(correct). Send the data to Google Cloud Pub/Sub, stream Cloud Pub/Sub to Google Cloud Dataflow, and store the data in Google BigQuery.

C. Send the data to Cloud Storage and then spin up an Apache Hadoop cluster as needed in Google Cloud Dataproc whenever analysis is required.

D. Export logs in batch to Google Cloud Storage and then spin up a Google Cloud SQL instance, import the data from Cloud Storage, and run an analysis as needed.

Overall explanation
B is more correct than other options so B is the answer. But if this is actual use case you have to deal with use Cloud BigTable instead of bigquery. So the pipeline will be like this. IOT-Devices -> Cloud Pub/Sub -> Cloud BigTable -> Cloud Data Studio (For real-time analytics)

##### You have Cloud Functions written in Node.js that pull messages from Cloud Pub/Sub and send the data to BigQuery. You observe that the message processing rate on the Pub/Sub topic is orders of magnitude higher than anticipated, but there is no error logged in Stackdriver Log Viewer. What are the two most likely causes of this problem? (Choose two.)
A. Publisher throughput quota is too small.

B. Total outstanding messages exceed the 10-MB maximum.

C(correct). Error handling in the subscriber code is not handling run-time errors properly.

D. The subscriber code cannot keep up with the messages.

E(correct). The subscriber code does not acknowledge the messages that it pulls.

Overall explanation
Answer: C, E Description: C, E: By not acknowleding the pulled message, this result in it be putted back in Cloud Pub/Sub, meaning the messages accumulate instead of being consumed and removed from Pub/Sub. The same thing can happen ig the subscriber maintains the lease on the message it receives in case of an error. This reduces the overall rate of processing because messages get stuck on the first subscriber. Also, errors in Cloud Function do not show up in Stackdriver Log Viewer if they are not correctly handled. A: No problem with publisher rate as the observed result is a higher number of messages and not a lower number. B: if messages exceed the 10MB maximum, they cannot be published. D: Cloud Functions automatically scales so they should be able to keep up.

##### Which of the following are examples of hyperparameters? (Select 2 answers.)
A(correct). Number of hidden layers

B(correct). Number of nodes in each hidden layer

C. Biases

D. Weights

Overall explanation
If model parameters are variables that get adjusted by training with existing data, your hyperparameters are the variables about the training process itself. For example, part of setting up a deep neural network is deciding how many "hidden" layers of nodes to use between the input layer and the output layer, as well as how many nodes each layer should use. These variables are not directly related to the training data at all. They are configuration variables. Another difference is that parameters change during a training job, while the hyperparameters are usually constant during a job. Weights and biases are variables that get adjusted during the training process, so they are not hyperparameters. Reference: https://cloud.google.com/ml-engine/docs/hyperparameter-tuning-overview

##### After migrating ETL jobs to run on BigQuery, you need to verify that the output of the migrated jobs is the same as the output of the original. You've loaded a table containing the output of the original job and want to compare the contents with output from the migrated job to show that they are identical. The tables do not contain a primary key column that would enable you to join them together for comparison.What should you do?
A. Select random samples from the tables using the RAND() function and compare the samples.

B. Select random samples from the tables using the HASH() function and compare the samples.

C(correct). Use a Dataproc cluster and the BigQuery Hadoop connector to read the data from each table and calculate a hash from non-timestamp columns of the table after sorting. Compare the hashes of each table.

D. Create stratified random samples using the OVER() function and compare equivalent samples from each table.

Overall explanation
C Using Cloud Storage with big data Cloud Storage is a key part of storing and working with Big Data on Google Cloud. Examples include: Loading data into BigQuery. Using Dataproc, which automatically installs the HDFS-compatible Cloud Storage connector, enabling the use of Cloud Storage buckets in parallel with HDFS. Using a bucket to hold staging files and temporary data for Dataflow pipelines. For Dataflow, a Cloud Storage bucket is required. For BigQuery and Dataproc, using a Cloud Storage bucket is optional but recommended. gsutil is a command-line tool that enables you to work with Cloud Storage buckets and objects easily and robustly, in particular in big data scenarios. For example, with gsutil you can copy many files in parallel with a single command, copy large files efficiently, calculate checksums on your data, and measure performance from your local computer to Cloud Storage.

##### MJTelco Case Study - Company Overview - MJTelco is a startup that plans to build networks in rapidly growing, underserved markets around the world. The company has patents for innovative optical communications hardware. Based on these patents, they can create many reliable, high-speed backbone links with inexpensive hardware. Company Background - Founded by experienced telecom executives, MJTelco uses technologies originally developed to overcome communications challenges in space. Fundamental to their operation, they need to create a distributed data infrastructure that drives real-time analysis and incorporates machine learning to continuously optimize their topologies. Because their hardware is inexpensive, they plan to overdeploy the network allowing them to account for the impact of dynamic regional politics on location availability and cost. Their management and operations teams are situated all around the globe creating many-to-many relationship between data consumers and provides in their system. After careful consideration, they decided public cloud is the perfect environment to support their needs. Solution Concept - MJTelco is running a successful proof-of-concept (PoC) project in its labs. They have two primary needs: ✑ Scale and harden their PoC to support significantly more data flows generated when they ramp to more than 50,000 installations. ✑ Refine their machine-learning cycles to verify and improve the dynamic models they use to control topology definition. MJTelco will also use three separate operating environments "" development/test, staging, and production "" to meet the needs of running experiments, deploying new features, and serving production customers. Business Requirements - ✑ Scale up their production environment with minimal cost, instantiating resources when and where needed in an unpredictable, distributed telecom user community. ✑ Ensure security of their proprietary data to protect their leading-edge machine learning and analysis. ✑ Provide reliable and timely access to data for analysis from distributed research workers ✑ Maintain isolated environments that support rapid iteration of their machine-learning models without affecting their customers. Technical Requirements - ✑ Ensure secure and efficient transport and storage of telemetry data ✑ Rapidly scale instances to support between 10,000 and 100,000 data providers with multiple flows each. ✑ Allow analysis and presentation against data tables tracking up to 2 years of data storing approximately 100m records/day ✑ Support rapid iteration of monitoring infrastructure focused on awareness of data pipeline problems both in telemetry flows and in production learning cycles. CEO Statement - Our business model relies on our patents, analytics and dynamic machine learning. Our inexpensive hardware is organized to be highly reliable, which gives us cost advantages. We need to quickly stabilize our large distributed data pipelines to meet our reliability and capacity commitments. CTO Statement - Our public cloud services must operate as advertised. We need resources that scale and keep our data secure. We also need environments in which our data scientists can carefully study and quickly adapt our models. Because we rely on automation to process our data, we also need our development and test environments to work as we iterate. CFO Statement - The project is too large for us to maintain the hardware and software required for the data and analysis. Also, we cannot afford to staff an operations team to monitor so many data feeds, so we will rely on automation and infrastructure. Google Cloud's machine learning will allow our quantitative researchers to work on our high-value problems instead of problems with our data pipelines. You need to compose visualizations for operations teams with the following requirements: ✑ The report must include telemetry data from all 50,000 installations for the most resent 6 weeks (sampling once every minute). ✑ The report must not be more than 3 hours delayed from live data. ✑ The actionable report should only show suboptimal links. ✑ Most suboptimal links should be sorted to the top. ✑ Suboptimal links can be grouped and filtered by regional geography. ✑ User response time to load the report must be <5 seconds. Which approach meets the requirements?
A. Load the data into Google Sheets, use formulas to calculate a metric, and use filters/sorting to show only suboptimal links in a table.

B. Load the data into Google BigQuery tables, write Google Apps Script that queries the data, calculates the metric, and shows only suboptimal rows in a table in Google Sheets.

C(correct). Load the data into Google Cloud Datastore tables, write a Google App Engine Application that queries all rows, applies a function to derive the metric, and then renders results in a table using the Google charts and visualization API.

D. Load the data into Google BigQuery tables, write a Google Data Studio 360 report that connects to your data, calculates a metric, and then uses a filter expression to show only suboptimal rows in a table.

##### The _________ for Cloud Bigtable makes it possible to use Cloud Bigtable in a Cloud Dataflow pipeline.
A(correct). Cloud Dataflow connector

B. DataFlow SDK

C. BiqQuery API

D. BigQuery Data Transfer Service

Overall explanation
The Cloud Dataflow connector for Cloud Bigtable makes it possible to use Cloud Bigtable in a Cloud Dataflow pipeline. You can use the connector for both batch and streaming operations. Reference: https://cloud.google.com/bigtable/docs/dataflow-hbase

##### What are two of the benefits of using denormalized data structures in BigQuery?
A. Reduces the amount of data processed, reduces the amount of storage required
Correct answer

B(correct). Increases query speed, makes queries simpler

C. Reduces the amount of storage required, increases query speed

D. Reduces the amount of data processed, increases query speed

Overall explanation
Denormalization increases query speed for tables with billions of rows because BigQuery's performance degrades when doing JOINs on large tables, but with a denormalized data structure, you don't have to use JOINs, since all of the data has been combined into one table. Denormalization also makes queries simpler because you do not have to use JOIN clauses. Denormalization increases the amount of data processed and the amount of storage required because it creates redundant data. Reference: https://cloud.google.com/solutions/bigquery-data-warehouse#denormalizing_data

##### MJTelco Case Study -Company Overview -MJTelco is a startup that plans to build networks in rapidly growing, underserved markets around the world. The company has patents for innovative optical communications hardware. Based on these patents, they can create many reliable, high-speed backbone links with inexpensive hardware.Company Background -Founded by experienced telecom executives, MJTelco uses technologies originally developed to overcome communications challenges in space. Fundamental to their operation, they need to create a distributed data infrastructure that drives real-time analysis and incorporates machine learning to continuously optimize their topologies. Because their hardware is inexpensive, they plan to overdeploy the network allowing them to account for the impact of dynamic regional politics on location availability and cost.Their management and operations teams are situated all around the globe creating many-to-many relationship between data consumers and provides in their system. After careful consideration, they decided public cloud is the perfect environment to support their needs.Solution Concept -MJTelco is running a successful proof-of-concept (PoC) project in its labs. They have two primary needs:✑ Scale and harden their PoC to support significantly more data flows generated when they ramp to more than 50,000 installations.✑ Refine their machine-learning cycles to verify and improve the dynamic models they use to control topology definition.MJTelco will also use three separate operating environments "" development/test, staging, and production "" to meet the needs of running experiments, deploying new features, and serving production customers.Business Requirements -✑ Scale up their production environment with minimal cost, instantiating resources when and where needed in an unpredictable, distributed telecom user community.✑ Ensure security of their proprietary data to protect their leading-edge machine learning and analysis.✑ Provide reliable and timely access to data for analysis from distributed research workers✑ Maintain isolated environments that support rapid iteration of their machine-learning models without affecting their customers.Technical Requirements -Ensure secure and efficient transport and storage of telemetry dataRapidly scale instances to support between 10,000 and 100,000 data providers with multiple flows each.Allow analysis and presentation against data tables tracking up to 2 years of data storing approximately 100m records/daySupport rapid iteration of monitoring infrastructure focused on awareness of data pipeline problems both in telemetry flows and in production learning cycles.CEO Statement -Our business model relies on our patents, analytics and dynamic machine learning. Our inexpensive hardware is organized to be highly reliable, which gives us cost advantages. We need to quickly stabilize our large distributed data pipelines to meet our reliability and capacity commitments.CTO Statement -Our public cloud services must operate as advertised. We need resources that scale and keep our data secure. We also need environments in which our data scientists can carefully study and quickly adapt our models. Because we rely on automation to process our data, we also need our development and test environments to work as we iterate.CFO Statement -The project is too large for us to maintain the hardware and software required for the data and analysis. Also, we cannot afford to staff an operations team to monitor so many data feeds, so we will rely on automation and infrastructure. Google Cloud's machine learning will allow our quantitative researchers to work on our high-value problems instead of problems with our data pipelines.Given the record streams MJTelco is interested in ingesting per day, they are concerned about the cost of Google BigQuery increasing. MJTelco asks you to provide a design solution. They require a single large data table called tracking_table. Additionally, they want to minimize the cost of daily queries while performing fine-grained analysis of each day's events. They also want to use streaming ingestion. What should you do?
A. Create a table called tracking_table and include a DATE column.
B(correct). Create a partitioned table called tracking_table and include a TIMESTAMP column.
C. Create sharded tables for each day following the pattern tracking_table_YYYYMMDD.
D. Create a table called tracking_table with a TIMESTAMP column to represent the day.

##### You work for a shipping company that uses handheld scanners to read shipping labels. Your company has strict data privacy standards that require scanners to only transmit recipients' personally identifiable information (PII) to analytics systems, which violates user privacy rules. You want to quickly build a scalable solution using cloud-native managed services to prevent exposure of PII to the analytics systems. What should you do?
A. Create an authorized view in BigQuery to restrict access to tables with sensitive data.
B. Install a third-party data validation tool on Compute Engine virtual machines to check the incoming data for sensitive information.
C. Use Stackdriver logging to analyze the data passed through the total pipeline to identify transactions that may contain sensitive information.
Your answer is correct
D(correct). Build a Cloud Function that reads the topics and makes a call to the Cloud Data Loss Prevention API. Use the tagging and confidence levels to either pass or quarantine the data in a bucket for review.

Overall explanation
Cloud Data Loss Prevention gives you the power to scan, discover, classify, and report on data from virtually anywhere. Cloud DLP has native support for scanning and classifying sensitive data in Cloud Storage, BigQuery, and Cloud Datastore and a streaming content API to enable support for additional data sources, custom workloads and applications. https://cloud.google.com/dlp/

##### You are building a model to make clothing recommendations. You know a user's fashion preference is likely to change over time, so you build a data pipeline to stream new data back to the model as it becomes available. How should you use this data to train the model?
A. Continuously retrain the model on just the new data.

B. Continuously retrain the model on a combination of existing data and the new data.

C. Train on the existing data while using the new data as your test set.

D. Train on the new data while using the existing data as your test set.

Overall explanation
Vote for B. In Recommendation System - Matrix stored in database - which store the users rating and other details like how much time user spent on that page.We generally recommend on basis of matrix. And In production that matrix updated (or model get retrained once a day or once a week) - Because there could be new users rating. or we can say new data. So model retrained fully i.e. on Existing Data + New Data => and generate a new matrix (user/item matrix)

##### You are integrating one of your internal IT applications and Google BigQuery, so users can query BigQuery from the application's interface. You do not want individual users to authenticate to BigQuery and you do not want to give them access to the dataset. You need to securely access BigQuery from your IT application. What should you do?
A. Create groups for your users and give those groups access to the dataset

B. Integrate with a single sign-on (SSO) platform, and pass each user's credentials along with the query request

C(correct). Create a service account and grant dataset access to that account. Use the service account's private key to access the dataset

D. Create a dummy user and grant dataset access to that user. Store the username and password for that user in a file on the files system, and use those credentials to access the BigQuery dataset

##### You want to automate execution of a multi-step data pipeline running on Google Cloud. The pipeline includes Cloud Dataproc and Cloud Dataflow jobs that have multiple dependencies on each other. You want to use managed services where possible, and the pipeline will run every day. Which tool should you use?
A. cron

B(correct). Cloud Composer

C. Cloud Scheduler

D. Workflow Templates on Cloud Dataproc

Overall explanation
B: Cloud Composer is a fully managed workflow orchestration service that empowers you to author, schedule, and monitor pipelines that span across clouds and on-premises data centres. https://cloud.google.com/composer/

##### You are building a new application that you need to collect data from in a scalable way. Data arrives continuously from the application throughout the day, and you expect to generate approximately 150 GB of JSON data per day by the end of the year. Your requirements are:✑ Decoupling producer from consumer✑ Space and cost-efficient storage of the raw ingested data, which is to be stored indefinitely✑ Near real-time SQL query✑ Maintain at least 2 years of historical data, which will be queried with SQLWhich pipeline should you use to meet these requirements?
A. Create an application that provides an API. Write a tool to poll the API and write data to Cloud Storage as gzipped JSON files.

B. Create an application that writes to a Cloud SQL database to store the data. Set up periodic exports of the database to write to Cloud Storage and load into BigQuery.

C. Create an application that publishes events to Cloud Pub/Sub, and create Spark jobs on Cloud Dataproc to convert the JSON data to Avro format, stored on HDFS on Persistent Disk.

D(correct). Create an application that publishes events to Cloud Pub/Sub, and create a Cloud Dataflow pipeline that transforms the JSON event payloads to Avro, writing the data to Cloud Storage and BigQuery.

##### You are designing a basket abandonment system for an ecommerce company. The system will send a message to a user based on these rules:✑ No interaction by the user on the site for 1 hour✑ Has added more than $30 worth of products to the basket✑ Has not completed a transactionYou use Google Cloud Dataflow to process the data and decide if a message should be sent. How should you design the pipeline?
A. Use a fixed-time window with a duration of 60 minutes.

B. Use a sliding time window with a duration of 60 minutes.

C(correct). Use a session window with a gap time duration of 60 minutes.

D. Use a global window with a time based trigger with a delay of 60 minutes.

Overall explanation
The correct answer is C. There are 3 windowing concepts in dataflow and each can be used for below use case 1) Fixed window 2) Sliding window and 3) Session window. Fixed window = any aggregation use cases, any batch analysis of data, relatively simple use cases. Sliding window = Moving averages of data Session window = user session data, click data and real time gaming analysis. The question here is about user session data and hence session window.

##### You have historical data covering the last three years in BigQuery and a data pipeline that delivers new data to BigQuery daily. You have noticed that when theData Science team runs a query filtered on a date column and limited to 30""90 days of data, the query scans the entire table. You also noticed that your bill is increasing more quickly than you expected. You want to resolve the issue as cost-effectively as possible while maintaining the ability to conduct SQL queries.What should you do?
A(correct). Re-create the tables using DDL. Partition the tables by a column containing a TIMESTAMP or DATE Type.

B. Recommend that the Data Science team export the table to a CSV file on Cloud Storage and use Cloud Datalab to explore the data by reading the files directly.

C. Modify your pipeline to maintain the last 30""90 days of data in one table and the longer history in a different table to minimize full table scans over the entire history.

D. Write an Apache Beam pipeline that creates a BigQuery table per day. Recommend that the Data Science team use wildcards on the table name suffixes to select the data they need.

Overall explanation
I will go with Option A, although at first instance I felt Option C would be correct. Option A : Because partitioning will help to address both the concerns mentioned in the question - i.e. faster query and reducing cost. Option C : Modifying the data pipeline to store last 30-90 days data would have possible, if there was a point mentioned that only the latest data (30-90 days) is kept and the older data - beyond 90 days is moved to the master table. Since that point is mot mentioned, we will land up having multiple - 30-90 days data in separate tables + the master table.

##### You are designing storage for two relational tables that are part of a 10-TB database on Google Cloud. You want to support transactions that scale horizontally.You also want to optimize data for range queries on non-key columns. What should you do?
A. Use Cloud SQL for storage. Add secondary indexes to support query patterns.
Your answer is incorrect

B. Use Cloud SQL for storage. Use Cloud Dataflow to transform data to support query patterns.

C. Use Cloud Spanner for storage. Add secondary indexes to support query patterns.

D. Use Cloud Spanner for storage. Use Cloud Dataflow to transform data to support query patterns.

Overall explanation
A is not correct because Cloud SQL does not natively scale horizontally. B is not correct because Cloud SQL does not natively scale horizontally. C is correct because Cloud Spanner scales horizontally, and you can create secondary indexes for the range queries that are required. D is not correct because Dataflow is a data pipelining tool to move and transform data, but the use case is centered around querying.

##### You are designing storage for 20 TB of text files as part of deploying a data pipeline on Google Cloud. Your input data is in CSV format. You want to minimize the cost of querying aggregate values for multiple users who will query the data in Cloud Storage with multiple engines. Which storage service and schema design should you use?
A. Use Cloud Bigtable for storage. Install the HBase shell on a Compute Engine instance to query the Cloud Bigtable data.

B. Use Cloud Bigtable for storage. Link as permanent tables in BigQuery for query.

C(correct). Use Cloud Storage for storage. Link as permanent tables in BigQuery for query.

D. Use Cloud Storage for storage. Link as temporary tables in BigQuery for query.

Overall explanation
answer C: BigQuery can access data in external sources, known as federated sources. Instead of first loading data into BigQuery, you can create a reference to an external source. External sources can be Cloud Bigtable, Cloud Storage, and Google Drive. When accessing external data, you can create either permanent or temporary external tables. Permanent tables are those that are created in a dataset and linked to an external source. Dataset-level access controls can be applied to these tables. When you are using a temporary table, a table is created in a special dataset and will be available for approxi- mately 24 hours. Temporary tables are useful for one-time operations, such as loading data into a data warehouse. "Dan Sullivan" Book

##### You are designing the database schema for a machine learning-based food ordering service that will predict what users want to eat. Here is some of the information you need to store:✑ The user profile: What the user likes and doesn't like to eat✑ The user account information: Name, address, preferred meal times✑ The order information: When orders are made, from where, to whomThe database will be used to store all the transactional data of the product. You want to optimize the data schema. Which Google Cloud Platform product should you use?
A(correct). BigQuery

B. Cloud SQL

C. Cloud Bigtable

D. Cloud Datastore

Overall explanation
Firebase is a documental DB so can have a schema but "Cloud Datastore" not. The question says it needs to "store" transactional data, not doing transaction operations and the data will be used for ML. For all these reasones BigQuery is the best choice.

##### Your neural network model is taking days to train. You want to increase the training speed. What can you do?
A. Subsample your test dataset.

B(correct). Subsample your training dataset.

C. Increase the number of input features to your model.

D. Increase the number of layers in your neural network.

Overall explanation
increase the number of layers will make the training slower https://www.quora.com/Is-there-a-specific-reason-why-a-neural-network-with-more-layers-might-perform-worse-than-a-network-with-fewer-layers https://towardsdatascience.com/how-to-train-neural-network-faster-with-optimizers-d297730b3713

##### You need to store and analyze social media postings in Google BigQuery at a rate of 10,000 messages per minute in near real-time. Initially, design the application to use streaming inserts for individual postings. Your application also performs data aggregations right after the streaming inserts. You discover that the queries after streaming inserts do not exhibit strong consistency, and reports from the queries might miss in-flight data. How can you adjust your application design?
A. Re-write the application to load accumulated data every 2 minutes.

B. Convert the streaming insert code to batch load for individual messages.

C. Load the original message to Google Cloud SQL, and export the table every hour to BigQuery via streaming inserts.

D(correct). Estimate the average latency for data availability after streaming inserts, and always run queries after waiting twice as long.

Overall explanation
Answer: D Description: The data is first comes to buffer and then written to Storage. If we are running queries in buffer we will face above mentioned issues. If we wait for the bigquery to write the data to storage then we won’t face the issue. So We need to wait till it’s written tio storage

##### What are all of the BigQuery operations that Google charges for?
A(correct). Storage, queries, and streaming inserts

B. Storage, queries, and loading data from a file

C. Storage, queries, and exporting data

D. Queries and streaming inserts

Overall explanation
Google charges for storage, queries, and streaming inserts. Loading data from a file and exporting data are free operations. Reference: https://cloud.google.com/bigquery/pricing
