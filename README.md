# infra-aws-nginx-scale

1. Create a launch configuration as described in the [docs](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-launch-config.html)

2. In order to ensure that all instances that are spawned are ngnix servers, make sure that the user data for the launch configuration that you are creating has:
```
#!/bin/bash
amazon-linux-extras install -y nginx1
systemctl start nginx
```
3. Build an AutoScaling Group on top of the launch configuration as desribed [here](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg.html)

4. Create a Load Balancer by following [ELB docs](https://docs.aws.amazon.com/elasticloadbalancing/latest/classic/elb-create-https-ssl-load-balancer.html)

5. Connect the AutoScaling group to the Load balancer created.

6. In your managed hosted zones (Route 53), add a Type A record for a DNS and have that point to your load balancer.
You can use the AWS Certificate Manager to get a [Public certificate](https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html) as well to get the HTTPS traffic flowing.

7. Access the site
```
http://<Route-53-A-Record-name>
https://<Route-53-A-Record-name>
```
