# fullstack_developer_capstone

## Set up the Python Runtime

- Change to the server directory:

<pre>
cd /home/project/xrwvm-fullstack_developer_capstone/server
</pre>

- Set up the virtual environment for the Django application to run in:

<pre>
pip install virtualenv
virtualenv djangoenv
source djangoenv/bin/activate
</pre>

- Install the necessary Python packages in the virtual environment:

<pre>
python3 -m pip install -U -r requirements.txt
</pre>

- Perform migrations to create necessary tables:

<pre>
python3 manage.py makemigrations
</pre>

- Run migration to activate models for the app:

<pre>
python3 manage.py migrate
</pre>

- Create tables for apps without migrations:

<pre>
python3 manage.py migrate --run-syncdb
</pre>

- Start the local development server:

<pre>
python3 manage.py runserver
</pre>

## Create a Superuser

<pre>
python3 manage.py createsuperuser
</pre>

## Build the Client-Side and Its Configuration

- Change to the client directory:

<pre>
cd /home/project/xrwvm-fullstack_developer_capstone/server/frontend
</pre>

- Install all required packages:

<pre>
npm install
</pre>

- Build the client:

<pre>
npm run build
</pre>

## Build and Run the Mongo Server (Mongoose and MongoDB)

- Change to the data files directory:

<pre>
cd /home/project/xrwvm-fullstack_developer_capstone/server/database
</pre>

- Build the Docker app:

<pre>
docker build . -t nodeapp
</pre>

- Run the server:

<pre>
docker-compose up
</pre>

## IBM Code Engine

- Create a new Code Engine project

- Use the Code Engine CLI (Command Line Interface)

- Deploy Sentiment Analysis on Code Engine as a Microservice:

    - Change to the microservices directory:
    
    <pre>cd xrwvm-fullstack_developer_capstone/server/djangoapp/microservices</pre>

    - Build the sentiment analyzer app:

    <pre>docker build . -t us.icr.io/${SN_ICR_NAMESPACE}/senti_analyzer</pre>

    - Push the Docker image:

    <pre>docker push us.icr.io/${SN_ICR_NAMESPACE}/senti_analyzer</pre>

    - Deploy the senti_analyzer application on Code Engine:

    <pre>ibmcloud ce application create --name sentianalyzer --image us.icr.io/${SN_ICR_NAMESPACE}/senti_analyzer --registry-secret icr-secret --port 5000</pre>
