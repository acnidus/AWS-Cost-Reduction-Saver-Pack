# AWS Cost Saver Pack 🚀

A comprehensive collection of scripts and tools to automatically reduce AWS costs by managing idle resources, cleaning up unused volumes, and providing cost monitoring.

**[📖 About this Project](about.md)** | **[☕ Support Development](https://buymeacoffee.com/acnidal)**

## 📋 What's Included

### Core Scripts
- **`stop_idle_instances.py`** - Automatically stops idle EC2 instances
- **`clean_unused_ebs.sh`** - Removes unattached EBS volumes
- **`daily_cost_report.py`** - Sends daily cost reports via email

### Additional Cost-Saving Scripts
- **`cleanup_snapshots.py`** - Manages old EBS snapshots
- **`optimize_rds.py`** - Stops non-production RDS instances during off-hours
- **`cleanup_logs.py`** - Removes old CloudWatch logs
- **`cost_alert.py`** - Sends alerts when costs exceed thresholds

## 🚀 Quick Start

### Prerequisites
- Python 3.7+
- AWS CLI configured with appropriate permissions
- Required Python packages (see requirements.txt)

### Installation
```bash
# Clone or download this package
cd AWS_Cost_Saver_Pack

# Install Python dependencies
pip install -r requirements.txt

# Configure AWS credentials
aws configure
```

### Basic Usage
```bash
# Stop idle instances
python3 scripts/stop_idle_instances.py

# Clean unused EBS volumes
bash scripts/clean_unused_ebs.sh

# Generate daily cost report
python3 scripts/daily_cost_report.py
```

## 📁 Directory Structure
```
AWS_Cost_Saver_Pack/
├── README.md                 # This file
├── requirements.txt          # Python dependencies
├── config/
│   ├── config.yaml          # Configuration file
│   └── email_template.html   # Email template for reports
├── scripts/
│   ├── stop_idle_instances.py
│   ├── clean_unused_ebs.sh
│   ├── daily_cost_report.py
│   ├── cleanup_snapshots.py
│   ├── optimize_rds.py
│   ├── cleanup_logs.py
│   └── cost_alert.py
├── logs/                     # Script execution logs
├── cron/                     # Cron job examples
└── docs/                     # Detailed documentation
    ├── SETUP.md
    ├── CONFIGURATION.md
    └── TROUBLESHOOTING.md
```

## ⚙️ Configuration

### AWS Permissions Required
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:DescribeInstances",
                "ec2:StopInstances",
                "ec2:DescribeVolumes",
                "ec2:DeleteVolume",
                "ce:GetCostAndUsage",
                "rds:DescribeDBInstances",
                "rds:StopDBInstance",
                "logs:DescribeLogGroups",
                "logs:DeleteLogGroup"
            ],
            "Resource": "*"
        }
    ]
}
```

### Environment Variables
```bash
export AWS_DEFAULT_REGION=us-east-1
export COST_ALERT_THRESHOLD=100
export EMAIL_RECIPIENTS="admin@company.com,finance@company.com"
export IDLE_THRESHOLD_HOURS=24
```

## 🔧 Advanced Setup

### Automated Execution with Cron
```bash
# Edit crontab
crontab -e

# Add these lines for automated execution
0 2 * * * /usr/bin/python3 /path/to/scripts/stop_idle_instances.py
0 3 * * * /bin/bash /path/to/scripts/clean_unused_ebs.sh
0 8 * * * /usr/bin/python3 /path/to/scripts/daily_cost_report.py
```

### Docker Support
```bash
# Build and run with Docker
docker build -t aws-cost-saver .
docker run -v ~/.aws:/root/.aws aws-cost-saver
```

## 📊 Monitoring and Logging

All scripts generate detailed logs in the `logs/` directory:
- Execution timestamps
- Actions taken
- Resources affected
- Cost savings achieved
- Error details (if any)

## 🛡️ Safety Features

- **Dry-run mode** available for testing
- **Resource tagging** to prevent accidental deletion
- **Whitelist/blacklist** for critical resources
- **Rollback capabilities** for major changes
- **Email notifications** for all actions

## 💰 Expected Cost Savings

Based on typical usage patterns:
- **EC2 instances**: 20-40% reduction in compute costs
- **EBS volumes**: 15-25% reduction in storage costs
- **RDS instances**: 30-50% reduction in database costs
- **Overall**: 15-30% reduction in total AWS bill

## 🆘 Support and Troubleshooting

- Check the `docs/TROUBLESHOOTING.md` file
- Review logs in the `logs/` directory
- Ensure AWS credentials are properly configured
- Verify required permissions are granted

## 📝 License

This project is provided as-is for educational and business use. Please review and test all scripts in a non-production environment before deployment.

## 🤝 Contributing

Feel free to submit improvements, bug reports, or additional cost-saving scripts!

## 👨‍💻 Creator & Support

**Tool created by:** [acnid.al@gmail.com](mailto:acnid.al@gmail.com)

If you find this tool helpful and want to support its development:

**[Buy Me a Coffee ☕](https://buymeacoffee.com/acnidal)**

Your support helps maintain and improve this project for the community!

---

**⚠️ Important**: Always test scripts in a development environment before running in production. These scripts can affect your AWS infrastructure and costs.
