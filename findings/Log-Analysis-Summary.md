# Apache Web Server Log Analysis Summary

## Overview

This project demonstrates foundational log analysis and security monitoring techniques using Apache web server logs on Ubuntu Linux. The objective was to investigate web traffic, analyze HTTP requests, identify failed access attempts, and review server operational events through access and error logs.

---

# Project Objectives

- Install and configure Apache Web Server
- Generate web traffic and log data
- Analyze Apache access logs
- Review Apache error logs
- Investigate HTTP status codes
- Identify failed requests
- Extract security-relevant information
- Document findings professionally

---

# Lab Environment

| Component | Details |
|------------|------------|
| Operating System | Ubuntu Linux |
| Web Server | Apache2 |
| Log Location | /var/log/apache2 |
| Access Log | access.log |
| Error Log | error.log |
| Analysis Tools | grep, awk, sort, uniq, less |

---

# Activities Performed

## Apache Deployment

Apache2 was installed and configured successfully.

Verified:

- Service installation
- Service startup
- Service availability
- Localhost connectivity

---

## Access Log Analysis

The Apache access log was examined to identify:

- Source IP addresses
- Request methods
- Requested URLs
- HTTP response codes
- User agents

Sample Log Entry:

```text
127.0.0.1 - - [08/Jun/2026] "GET / HTTP/1.1" 200
```

---

## HTTP 404 Investigation

Several non-existent URLs were intentionally requested to generate 404 events.

Observed Requests:

```text
/admin
/login
/test
/secret
```

Total 404 Errors:

```text
5
```

---

## Source IP Analysis

Top Source IP:

```text
127.0.0.1
```

Total Requests:

```text
22
```

The observed traffic originated from localhost due to the isolated lab environment.

---

## URL Request Analysis

Most Requested Resource:

```text
/
```

Additional Resources:

```text
/admin
/login
/test
/secret
/favicon.ico
/icons/ubuntu-logo.png
```

---

## Error Log Analysis

Apache error logs were reviewed to identify service-related issues.

Observed Messages:

```text
AH00489: Apache configured -- resuming normal operations
AH00094: Command line: '/usr/sbin/apache2'
```

Result:

- No critical errors detected
- No service failures observed
- Apache operating normally

---

# Key Findings

| Finding | Result |
|-----------|-----------|
| Apache Running | Yes |
| Access Logs Available | Yes |
| Error Logs Available | Yes |
| Top Source IP | 127.0.0.1 |
| Total Requests | 22 |
| Total 404 Errors | 5 |
| Critical Errors Found | No |
| Suspicious URLs Observed | Yes |

---

# Security Relevance

This project demonstrates practical skills used by:

- SOC Analysts
- Security Operations Engineers
- Cloud Security Engineers
- Blue Team Analysts
- Incident Responders

Core competencies demonstrated:

- Linux Administration
- Log Analysis
- Security Monitoring
- Threat Detection
- Event Investigation
- Security Reporting

---

# Lessons Learned

- Apache logs provide valuable security telemetry.
- HTTP status codes help identify anomalies.
- Error logs assist with troubleshooting and monitoring.
- Command-line tools can rapidly extract security insights.
- Log analysis is a critical skill for cloud and security professionals.

---

# Conclusion

The Apache Web Server Log Analysis project successfully demonstrated the ability to collect, analyze, and interpret web server logs using Linux tools. Through access log investigation, error log review, and security findings documentation, the project provided hands-on experience in security monitoring and incident investigation processes commonly used in modern SOC and Cloud Security environments.
