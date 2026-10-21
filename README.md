# learner-lab-data-science
Open lab sequences for teaching cloud computing to data science students on AWS Academy Learner Lab: an undergraduate serverless data pipeline and a graduate course in cloud foundations. Includes lab guides, datasets, and verification and cleanup scripts. 
# Learner Lab for Data Science

Open lab sequences for teaching cloud computing to data science students on [AWS Academy Learner Lab](https://aws.amazon.com/training/awsacademy/). Two eight-lab courses are included:

- **Undergraduate:** students build one serverless data engineering pipeline, stage by stage.
- **Graduate (DTSC620, Cloud Foundations):** each lab poses an infrastructure decision for a data team in a fictional city, Riverbend.

The labs treat Learner Lab's fixed budget and restricted permissions as things to learn, not just limits to work around. Students probe what their role can and can't do, set budget alerts before building anything, and finish every lab with a cleanup script that proves nothing is left running.

These materials accompany the talk *Constraints as Curriculum: Two AWS Learner Lab Sequences for Undergraduate and Graduate Data Science* [SDSS 2027, link once accepted].

## What's included

| Folder | Contents |
| --- | --- |
| `dtsc620-graduate/` | Eight lab guides, datasets, and the verification, cleanup, and helper scripts for each lab |
| `[ug-course-number]-undergraduate/` | Eight lab guides, starter code, and scripts for the weather data pipeline |
| `docs/` | Instructor setup notes and cost estimates |

Answer keys, solution code, and rubrics with expected answers are kept in a separate private repository. See [Instructor materials](#instructor-materials).

## Graduate course: DTSC620 Cloud Foundations

An asynchronous course for data science and AI graduate students. Labs build on each other: the S3 bucket and VPC students create early are reused in later labs.

| Lab | Topic | What students do | Time |
| --- | --- | --- | --- |
| 1 | IAM, budgets, and S3 | Set budget alerts, probe what the lab role allows, protect raw data with a bucket policy, and recover an overwritten file with versioning | ~60 min |
| 2 | VPC and a web server | Build a VPC with public and private subnets in two Availability Zones and launch a web server that installs itself from S3 | ~50 min |
| 3 | EC2 and Python | Launch, monitor, and resize an instance; run pandas over Session Manager; compare AWS quotas with Learner Lab's limits | ~70 min |
| 4 | Serverless data quality | Trigger a Lambda function from S3 uploads through EventBridge to profile each CSV for missing values, broken rows, and duplicates | ~55 min |
| 5 | Elastic Beanstalk | Deploy a house sales dashboard, point it at new data, find a trend that reverses within categories, and release a second version | ~60 min |
| 6 | EBS vs. S3 | Choose storage for 1.5 million smart-meter readings, measure read speeds, and restore a snapshot in another Availability Zone | ~60 min |
| 7 | RDS PostgreSQL | Move house sales into a managed database, connect a web app, and query it from pandas; optional Multi-AZ failover | ~70 min (+25 optional) |
| 8 | Load balancing and Auto Scaling | Put a bootstrap price estimator behind a load balancer and watch Auto Scaling respond to the load | ~75 min |

## Undergraduate course: [UG COURSE NUMBER AND TITLE]

Students build an event-driven pipeline across eight labs:

1. Lambda functions ingest weather data from a public API.
2. A second function flattens the nested JSON.
3. A third function enriches records with business rules.
4. Amazon SNS monitors pipeline functionality.
5. Results are stored in DynamoDB and served to a website.
6. Athena and RDS support analytical queries.

[ADD A LAB TABLE MATCHING THE GRADUATE ONE.]

## Using these labs

**Requirements:**

- Your institution must be an AWS Academy member, and you must be an approved instructor. See Strain et al. (2025) for an overview of onboarding.
- Create a Learner Lab course for each class section.
- The labs assume the `us-east-1` Region and a $50 budget per student.

**Setup:** Each lab guide tells students which files to copy into their own S3 bucket. Scripts are run from AWS CloudShell, so students need nothing installed locally.

**Grading:** Every lab ends with a `verify-labN.sh` script. Students run it in CloudShell, and it checks their resources by name and prints a pass/fail summary. Students submit screenshots of that output, plus checkpoint screenshots showing their account name, which makes grading practical for large or asynchronous classes.

**Cost:** Instructor test runs cost about $[X] per student for the graduate sequence and $[X] for the undergraduate sequence. The most expensive resources are a NAT gateway (Lab 2), an RDS database (Lab 7), and a load balancer (Lab 8), which bill by the hour. Each of those labs ends with a required cleanup script that confirms everything was removed.

**Safety:** Learner Lab terminates instances above its limits and deactivates accounts that run 20 or more instances at once. Lab 8 caps Auto Scaling at three instances, requires a preflight check, and gives students a one-line emergency stop. Remind students never to use the Learner Lab **Reset** button, which permanently deletes all their work.

AWS changes its console and Learner Lab changes its permissions over time. Test each lab in a fresh Learner Lab account before your term starts.

## Instructor materials

Answer keys, solution code, and detailed rubrics are available to instructors. Email [jeff.eicher@eastern.edu](mailto:jeff.eicher@eastern.edu) from your institutional address with your course name, and I'll add you to the private repository.

Please don't post solutions publicly.

## License

[CC BY 4.0]. You're welcome to adapt these labs for your own courses with attribution.

## How to cite

> Eicher, J. ([YEAR]). *Learner Lab for Data Science: Open lab sequences for undergraduate and graduate cloud computing courses* [Course materials]. GitHub. [REPOSITORY URL]

## Related work

- Strain, J., Marquardson, J., & Gomillion, D. L. (2025). Conquer the cloud: Effectively using the Amazon Web Services Academy Learner Lab for information systems education. *Information Systems Education Journal, 23*(6), 19–36. https://doi.org/10.62273/FWMT9408
- Goteng, G. L., Shohel, M. M. C., & Tariq, F. (2022). Enhancing student employability in collaboration with the industry: Case study of a partnership with Amazon Web Services Academy. *Education Sciences, 12*(6), 366. https://doi.org/10.3390/educsci12060366

## Contact

Jeff Eicher, Assistant Professor of Data Science, Eastern University
[jeff.eicher@eastern.edu](mailto:jeff.eicher@eastern.edu)

Issues and pull requests that fix errors or update steps for console changes are welcome.
