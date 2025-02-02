# End-to-End-EKS
**Prerequisites**
Install kubectl using curl 
curl.exe -LO "https://dl.k8s.io/release/v1.32.0/bin/windows/amd64/kubectl.exe"
kubectl version --client
**
**Then install eksctl**
Step 1: Use the Correct Download URL
It seems that the file is not being downloaded correctly because of an incorrect URL. Let's start fresh and get the proper download link directly from GitHub.

Go to the eksctl releases page on GitHub:

https://github.com/weaveworks/eksctl/releases
Find the latest version (e.g., 0.133.0) and click on it.

In the "Assets" section of the release, look for the eksctl_Linux_amd64.tar.gz file. Right-click the link and choose "Copy Link Address."

Step 2: Download the Correct File
Now, use the copied link to download the correct file with curl. Paste the URL you copied inside the curl command:

bash
Copy
curl -LO <paste-correct-link-here>
For example:

bash
Copy
curl -LO https://github.com/weaveworks/eksctl/releases/download/0.133.0/eksctl_Linux_amd64.tar.gz
This should download the correct .tar.gz file.

Step 3: Verify the Download
Check if the file is the correct format:

bash
Copy
file eksctl_Linux_amd64.tar.gz
It should say something like gzip compressed data if it’s correct.

Step 4: Extract the File
Once you’ve confirmed that the file is in the correct format, extract it:

bash
Copy
tar -xvzf eksctl_Linux_amd64.tar.gz -C /tmp
Step 5: Move the Binary and Verify Installation
Finally, move the eksctl binary to a directory in your PATH:

bash
Copy
sudo mv /tmp/eksctl /usr/local/bin/
Verify that eksctl is correctly installed:

bash
Copy
eksctl version

**Install AWS cli**
Go through google and install
aws configure
in this provide access and secret access ket through secret management and check aws version
