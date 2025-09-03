Follow this tutorial: https://repost.aws/knowledge-center/send-ec2-nvidia-gpu-metrics-cloudwatch

1) Create a file : sudo touch /opt/aws/amazon-cloudwatch-agent/etc/config.json
2) Use content of config.json to populate this file.
3) Execute command : sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/etc/config.json -s