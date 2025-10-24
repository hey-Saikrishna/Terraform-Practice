
provider "aws" {
  region = "us-east-1" 
}

# Create Security Group

resource "aws_security_group" "allow_ssh" {
  name        = "allow_ssh"
  description = "Allow SSH inbound traffic"

  ingress {
    description = "SSH from anywhere"
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }

  tags = {
    Name = "allow_ssh"
  }
}

# Create EC2 Instance

resource "aws_instance" "my_ec2" {
  ami           = "ami-0360c520857e3138f" 
  instance_type = "t3.micro"              
  key_name      = "N_Virginia_keypair"
  security_groups = [aws_security_group.allow_ssh.name]

  tags = {
    Name = "MyTerraformEC2"
  }
}

# Output Instance Info

output "instance_public_ip" {
  value = aws_instance.my_ec2.public_ip
}

output "instance_id" {
  value = aws_instance.my_ec2.id
}
