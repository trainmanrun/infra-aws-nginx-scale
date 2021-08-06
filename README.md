# infra-aws-nginx-scale

1. Follow this to create a launch configuration
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-launch-config.html
- Ensure that the user data is:
```
#!/bin/bash
amazon-linux-extras install -y nginx1
systemctl start nginx
```

2. Create an AutoScaling Group by following this
- https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg.html

3. Connect the AutoScaling group to the Load balancer created [previously](https://github.com/trainmanrun/infra-aws-nginx-lb)

4. Access the site
```
http://<Route-53-A-Record-name>
https://<Route-53-A-Record-name>
```
