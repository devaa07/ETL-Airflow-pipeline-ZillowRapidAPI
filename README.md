# ZillowRapidAPI_pipeline_proj
ETL pipleline using Airflow



# Step 1: Creating IAM User and generate Access keys for the user

# Step 2: Creating EC2 instance with t2.medium as recommended instance_type
          SG: Allow SSH traffic from anywhere
              Allow HTTPS traffic from the internet
              Allow HTTP traffic from the internet
              Custom TCP with 8080 as port and allow-Anywhere (Inbound-rules)

# Step 3: Connect to EC2 instance and install the below modules/packages.
          sudo apt update
          sudo apt install python3-pip
          sudo apt install python3.10-venv
          python3 -m venv RapiAPI_venv
          source RapiAPI_venv/bin/activate
          pip install --upgrade awscli
          sudo pip install apache-airflow
          airflow standalone
          pip install apache-airflow-providers-amazon

# Stop 4:  login with Airflow web interface with username and password
            http://54.157.235.28:8080/login/

# Step 5: Connect remotley with AWS EC2 using SSH from VSCode



# Step 6: Run airflow standalone and see hte list of DAG's

# Step 7: Go to htpps://rapidapi.com/hub/ and search for zillow API

<img width="554" alt="Screen Shot 2023-12-30 at 1 47 43 AM" src="https://github.com/devaa07/ZillowRapidAPI_pipeline_proj/assets/126756574/e361706a-1e75-40dc-87fe-68ebfff19461">

# Step 8: Write the code for the DAG
          RapidAnalytics.py

# Step 9: create a Role and give AWSS3FullAccess to EC2 and assigen this role to EC2 instance

# Step 10: 
  Create Lambda Function copyRawJsonFile-LambdaFunction with Python 3.10 as run-time and create a role with AWSS3FullAccess policy to and give access to Lambda and also assign 
   AWSLambdaBasicExecutionRole add S3Put as event for this lambda. Also, increase the timeout to 5 mins under configuration
      -> Refer the relevant code for this function in the repo
  
  Create Lambda Function transformation-convert-to-csv-lambdaFunction with Python 3.10 as run-time and create a role with AWSS3FullAccess policy to and give access to Lambda and also     assign AWSLambdaBasicExecutionRole add S3Put as event for this lambda. Also, increase the timeout to 5 mins under configuration. Add the Pandas modulde as the layer to this lambda
       -> Refer the relevant code for this function in the repo
     
# Step 11: Add a relevant S3 trigger to both lambda functions 

# Step 12: Add the AWS S3 connection in the Airflow connections

<img width="1397" alt="Screen Shot 2023-12-30 at 2 03 04 AM" src="https://github.com/devaa07/ZillowRapidAPI_pipeline_proj/assets/126756574/22d49738-f562-43b1-91b5-dec7b42599ed">

# Step 13: Add the S3ToRedshiftOperator as a task inside DAG and Create the Redshift Cluster and also, create the table

<img width="452" alt="Screen Shot 2023-12-30 at 1 36 47 AM" src="https://github.com/devaa07/ZillowRapidAPI_pipeline_proj/assets/126756574/63019c21-94a9-4b6f-a137-f586607ee534">

# Step 14: Add the Redshift connection Id inside Airflow connection

<img width="1398" alt="Screen Shot 2023-12-30 at 2 09 40 AM" src="https://github.com/devaa07/ZillowRapidAPI_pipeline_proj/assets/126756574/900c4c8b-c6f7-486b-bfc0-94621fae175f">

# Step 15: Update IAM role with AWSRedshiftFullAccess  

# Step 16: Trigger the DAG and everything is running successfuly in the DAG Workflow

<img width="1427" alt="Screen Shot 2023-12-30 at 2 12 20 AM" src="https://github.com/devaa07/ZillowRapidAPI_pipeline_proj/assets/126756574/1b0ea2ac-4ce3-4799-8066-50f254f4a662">

# Step 17: Signup for the free QuickSight version and create the quicksight account

# Step 18:  Add the RedShift data soource and connect to the required table

![Screen Shot 2023-12-30 at 2 14 21 AM](https://github.com/devaa07/ZillowRapidAPI_pipeline_proj/assets/126756574/cb68dcb7-1a99-47b9-99ed-c65563cc9857)

# Step 19: Play with the Quicksight Analytics and analyze our data

<img width="1459" alt="Screen Shot 2023-12-30 at 1 04 06 AM" src="https://github.com/devaa07/ZillowRapidAPI_pipeline_proj/assets/126756574/b1bef7ce-6127-4c52-94bc-6d884d60d946">













            
