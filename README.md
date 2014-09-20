aws-scratch
===========

Scratch pad for learning AWS






-- Create key pair
aws ec2 create-key-pair --key-name e9002B --query 'KeyMaterial' --output text 

-- Create Window instance
aws ec2 run-instances --image-id ami-dc65c8b4 --count 1 --instance-type t2.micro --key-name e9002C --security-group-ids sg-xxxx --subnet-id subnet-bd66afca --associate-public-ip-address

-- Tag it

aws ec2 create-tags --resources i-xxxxxxx  --tags  Key=Name,Value=E90_Assignment_02_B_Windows

-- Get Status

aws ec2 describe-instance-status --instance-ids i-xxxxxxxx


-- Update Security Group - Add 3389
aws ec2 authorize-security-group-ingress --group-id sg-xxxxxxxx --protocol tcp --port 3389 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-id sg-xxxxxxxx --protocol tcp --port  8080 --cidr 0.0.0.0/0
-- Note also updaet Windows firewall

-- Get Windows password
aws ec2 get-password-data --instance-id  i-xxxxxxxxx --priv-launch-key  ./e9002B.pem


Notes
aws ec2 create-key-pair --key-name e9002A --query 'KeyMaterial' --output text | out-file -encoding ascii -filepath e9002A.pem
