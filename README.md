# Terraform-modules-VPC-and-S3-bucket-with-backend-storage

* Create your Terraform project folder
  <img width="1920" height="1069" alt="image" src="https://github.com/user-attachments/assets/fd56a2dd-8266-4de1-bf79-7dfcb2e5ed54" />

* Navigate to the Project folder
  <img width="1113" height="337" alt="image" src="https://github.com/user-attachments/assets/6638067a-a855-4f21-afb0-61bca762144f" />

* Create directories for the VPC and S3 modules
  <img width="1217" height="723" alt="image" src="https://github.com/user-attachments/assets/ea63e135-7db0-4637-b65d-e6adf7c3e290" />

* Create the main Terraform configuration file
  <img width="1920" height="1008" alt="image" src="https://github.com/user-attachments/assets/a4f60970-c175-4e09-8bda-23cea0142c2d" />

* Run `terraform init` to install all new resources
  <img width="1552" height="744" alt="image" src="https://github.com/user-attachments/assets/a3e2c495-5fea-436b-9784-5222dc476251" />

* Run `terraform apply -auto-approve` 
  <img width="1920" height="1008" alt="image" src="https://github.com/user-attachments/assets/14d4891b-3ab3-4d06-a0c3-dec8e088479f" />

* Confirm resources have been created for S3 and VPC
  
  <img width="1920" height="827" alt="image" src="https://github.com/user-attachments/assets/84f584c1-0b24-43b1-b7b0-1780e16885d0" />

   <img width="1920" height="827" alt="image" src="https://github.com/user-attachments/assets/b2b873c3-d99f-455a-aef8-96d47c8ab2d5" />


MY CHALLENGES :
1. Trying to create the resources with the backend state lock it was not working .
2. I got an AuthorizationHeaderMalformed error because the region I had specified in my backend.tf file didn't match the region where my AWS credentials were set up
3. I used force_destroy = true in my S3 bucket configuration to easily clean up my resources during development
   
SOLUTION :
1. Terraform needs to use the S3 bucket and DynamoDB table before it can run, But if those resources don’t exist yet, it can’t use them — and can’t lock the state.
2. I crosschecked the regions in my config and the region on my Provider resource in the root folder main.tf
3. I will remember to use prevent_destroy = true for important production resources. 




