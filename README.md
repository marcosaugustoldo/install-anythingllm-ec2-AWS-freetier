![https://raw.githubusercontent.com/Mintplex-Labs/anything-llm/master/images/wordmark.png](https://raw.githubusercontent.com/Mintplex-Labs/anything-llm/master/images/wordmark.png)

# Install an Anything LLM container on an AWS Free Tier EC2 Instance

Let's create a container for Anything LLM on the AWS instance you created based on [this tutorial](https://github.com/marcosaugustoldo/install-aws/blob/main/README.md) .

Here's a step-by-step tutorial:

## Step 1: Create the anythingllm directory

Create a new directory called `anythingllm` in the `home/ec2-user` directory using the command:
```
mkdir ~/anythingllm
```
Then, navigate to the newly created directory:
```
cd ~/anythingllm
```
## Step 2: Create the docker-compose.yml file

Create a new file called `docker-compose.yml` in the current directory with the following content:
```
version: '3'
services:
  anythingllm:
    image: mintplexlabs/anythingllm:master
    ports:
      - "3001:3001"
    volumes:
      - anythingllm-data:/app/data
    restart: always

volumes:
  anythingllm-data:
```
## Step 3: Start the container

Run the command `docker-compose up -d` to start the container in the background:
```
docker-compose up -d
```
## Step 4: Verify the container is running

Verify the container is running using the command `docker-compose ps`:
```
docker-compose ps
```
## Step 5: Access Anything LLM

Access Anything LLM at `http://your-ip-address:3001` (replace `your-ip-address` with the IP address of your AWS instance).

## Additional Tips

* Make sure port 3001 is open in the security group of your AWS instance.
* If you need to store data for Anything LLM, ensure the `anythingllm-data` volume is configured correctly.
* If you have a domain and want a subdomain to point to `http://your-ip-address:3001`, follow [this tutorial](https://github.com/Mintplex-Labs/anything-llm/blob/master/cloud-deployments/aws/cloudformation/aws_https_instructions.md) by [timothycarambat](https://github.com/timothycarambat)
