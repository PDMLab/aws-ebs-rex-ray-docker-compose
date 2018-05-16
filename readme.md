This sample shows how to use [REX-Ray](https://rexray.io/) with [AWS EBS](https://aws.amazon.com/ebs/) and [Docker Compose](https://docs.docker.com/compose/)

This sample requires Docker version 1.13, where the `docker plugin` feature has been introduced.
If you want to use the long syntax to specify volumes for a service, Docker Compose schema version 2.3 hence Docker version 17.06.0+ are required.

Install REX-Ray as a Docker plugin:
`docker plugin install rexray/ebs:0.11.2 EBS_ACCESSKEY=AWS_ACCESS_KEY_ID EBS_SECRETKEY=AWS_SECRET_ACCESS_KEY`

Create an AWS EBS volume
`aws ec2 create-volume --size 10 --region eu-central-1 --availability-zone eu-central-1a --volume-type gp2 --tag-specifications 'ResourceType=volume,Tags=[{Key=Name,Value=test-volume}]'`

For Docker Compose schema version 2.1, start the `busybox` container using Docker Compose this way:
`docker-compose up`

Expected output:

```
Creating busy ... done
Attaching to busy
busy    | total 8
busy    | drwx------    2 root     root          4096 May 12 19:15 .
busy    | drwxr-xr-x   19 root     root          4096 May 12 19:30 ..
busy exited with code 0
```

For Docker Compose schema version 2.3+, start the `busybox` container using Docker Compose this way:
`docker-compose -f docker-compose_2.3 up`

Expected output:

```
Creating busy ... done
Attaching to busy
busy    | total 8
busy    | drwx------    2 root     root          4096 May 12 19:15 .
busy    | drwxr-xr-x   19 root     root          4096 May 12 19:30 ..
busy exited with code 0
```