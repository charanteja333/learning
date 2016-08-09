 #Learning AWS


* `aws ec2 run-instances --image-id=ami-669bd00c --instance-type=m3.xlarge --key-name=charan --count=1 --block-device-mappings '[{ "DeviceName": "/dev/sda1","Ebs":{"DeleteOnTermination": true,"VolumeSize":50}}]'` -- Creating a instance in AWS
* `aws ec2 modify-image-attribute --image-id ami-38b1fb52 --launch-permission "{\"Add\":[{\"Group\":\"all\"}]}"` -- Make a AMI public
*  `aws ec2 describe-image-attribute --image-id ami-38b1fb52 --attribute launchPermission` -- Check the launch permission attribute