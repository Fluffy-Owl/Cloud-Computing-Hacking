# Cloud-Computing-Hacking



---
# Perform S3 bucket enumeration using various S3 bucket enumeration tools

**1. Enumerate S3 buckets using lazys3**

lazys3 is a Ruby script tool that is used to brute-force AWS S3 buckets using different permutations. This tool obtains the publicly accessible S3 buckets and also allows you to search the S3 buckets of a specific company by entering the company name.

1. `sudo su`
2. `cd lazys3-master/`
3. `ls`
4. `ruby lazys3.rb`
5. A list of public S3 buckets is displayed
6. Press **Ctrl+Z** to stop the script.
7. You can search the S3 buckets of specific company. To do so, type ruby lazys3.rb [Company] and press Enter. [Here, the target company name is HackerOne; you can enter the company name of your choice.]
8. The result appears, showing the obtained list of S3 buckets of the specified company.
9. Press Ctrl+Z to stop running the script.



**2. Enumerate S3 Buckets using S3Scanner**

S3Scanner is a tool that finds the open S3 buckets and dumps their contents. It takes a list of bucket names to check as its input. The S3 buckets that are found are output to a file. The tool also dumps or lists the contents of “open” buckets locally.

1. `sudo su`
2. `cd S3Scanner/`
3. In the S3Scanner folder, type `pip3 install -r requirements.txt` and press Enter to install the required dependencies.
4. After the successful installation of the dependencies, in the terminal window, type `python3 ./s3scanner.py sites.txt` and press Enter to run the tool.
5. Here, sites.txt is a text file containing the target website URL that is scanned for open S3 buckets. You can edit the sites.txt file to enter the target website URL of your choice.
6. The result appears, displaying a list of public S3 buckets. You might encounter the following error: “AWS credentials not configured.” Ignore the error, as we will install and configure the AWS CLI in the next lab.


You can also use other S3 bucket enumeration tools such as S3Inspector (https://github.com), s3-buckets-bruteforcer (https://github.com), Mass3 (https://github.com), Bucket Finder (https://digi.ninja), and s3recon (https://github.com) to perform S3 bucket enumeration for a target website or company.

---
# Exploit S3 Buckets

**1. Exploit Open S3 Buckets using AWS CLI**




---
# Perform Privilege Escalation to Gain Higher Privileges

**1. Escalate IAM User Privileges by Exploiting Misconfigured User Policy**


1. `sudo su`
2. `cd`
3. `aws configure`
4. Enter the details of the target IAM user’s access key in the AWS Access Key ID field and press Enter. Similarly, in the AWS Secret Access Key filed, enter the target IAM user’s secret access key and press Enter.
5. In the Default region name field, type `us-east-2` and press Enter. In the Default output format field, type `json` and press Enter.
6. After configuring the AWS CLI, we create a user policy and attach it to the target IAM user account to escalate the privileges.
7. In the terminal window, type `vim user-policy.json` and press Enter.
8. A command line text editor appears; press I and type the script given below:

{

"Version":"2012-10-17",

"Statement": [
{

    "Effect":"Allow",

    "Action":"*",

    "Resource":"*"

}
]
}

9. After entering the script given in the previous step, press the Esc button. Then, type :wq! and press Enter to save the text document
10. Now, we will attach the created policy (user-policy) to the target IAM user’s account. To do so, type aws iam create-policy --policy-name user-policy --policy-document file://user-policy.json and press Enter.
11. The created user policy is displayed, showing various details such as PolicyName, PolicyId, and Arn.






