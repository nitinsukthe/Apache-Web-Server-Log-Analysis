# Security Findings Report

## Project Information

| Field | Value |
|---------|---------|
| Project Name | Apache Web Server Log Analysis |
| Analyst | Nitin Sukthe |
| Environment | Ubuntu Linux |
| Web Server | Apache2 |
| Log Sources | access.log, error.log |
| Analysis Date | June 2026 |

---

# Executive Summary

This project focused on analyzing Apache web server logs to identify web traffic patterns, failed requests, and potential indicators of suspicious activity. Access logs and error logs were examined using Linux command-line tools to investigate HTTP requests, identify 404 errors, and evaluate overall server health.

The analysis demonstrated practical Security Operations Center (SOC) skills including log investigation, event correlation, threat identification, and security reporting.

---

# Scope

The following log sources were analyzed:

- Apache Access Log (`access.log`)
- Apache Error Log (`error.log`)

Analysis objectives included:

- Identifying source IP addresses
- Investigating HTTP status codes
- Detecting failed requests
- Reviewing server error messages
- Documenting security observations

---

# Finding 1: HTTP 404 Errors Detected

## Description

Several requests resulted in HTTP 404 (Not Found) responses.

Observed URLs:

```text
/admin
/login
/test
/secret
/favicon.ico
```

## Evidence

```text
127.0.0.1 GET /test HTTP/1.1 404
127.0.0.1 GET /admin HTTP/1.1 404
127.0.0.1 GET /login HTTP/1.1 404
127.0.0.1 GET /secret HTTP/1.1 404
```

## Risk Assessment

In production environments, repeated requests to administrative or hidden endpoints may indicate:

- Directory enumeration
- Automated vulnerability scanning
- Reconnaissance activity
- Unauthorized access attempts

## Severity

**Low (Lab Environment)**

**Medium (Production Environment)**

---

# Finding 2: Top Requesting Source IP

## Description

Request frequency analysis identified the most active source IP address.

## Evidence

```text
22 127.0.0.1
```

## Analysis

All traffic originated from localhost because the project was performed in a controlled lab environment.

In enterprise environments, analysts would investigate:

- High-volume source IPs
- Repeated authentication attempts
- Unusual geographic locations
- Known malicious IP indicators

## Severity

Informational

---

# Finding 3: Most Requested Resource

## Evidence

```text
16 /
```

## Analysis

The root web page generated the highest volume of requests during testing.

Additional observed requests:

```text
/admin
/login
/test
/secret
/icons/ubuntu-logo.png
/favicon.ico
```

## Security Relevance

Monitoring frequently requested resources helps identify:

- Normal traffic patterns
- Brute-force activity
- Enumeration attempts
- Application misuse

---

# Finding 4: Apache Error Log Review

## Description

Apache error logs were reviewed for critical service issues.

## Evidence

```text
AH00489: Apache configured -- resuming normal operations
AH00094: Command line: '/usr/sbin/apache2'
```

## Analysis

No evidence was identified for:

- Service crashes
- Permission failures
- Configuration errors
- Application failures

Apache started and operated normally throughout testing.

## Severity

Informational

---

# Security Recommendations

## Monitoring

- Continuously monitor Apache access logs.
- Investigate recurring 404 errors.
- Track unusual URL requests.

## Detection

- Configure SIEM alerts for repeated failed requests.
- Monitor for directory enumeration attempts.
- Detect unusual spikes in request volume.

## Hardening

- Restrict access to administrative interfaces.
- Enable centralized logging.
- Regularly review web server logs.

## Incident Response

- Investigate suspicious source IPs.
- Correlate web logs with authentication logs.
- Escalate repeated reconnaissance activity.

---

# Conclusion

Apache log analysis successfully identified web traffic activity, failed requests, and server operational events. The project demonstrated practical experience in Linux log analysis, web server monitoring, threat detection, and security reporting. These skills align closely with SOC Analyst, Security Operations Engineer, and Cloud Security Engineer responsibilities.
