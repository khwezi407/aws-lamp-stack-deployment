# Troubleshooting Log

This document records the bugs encountered while building the LAMP deployment script, their root causes, and how they were fixed.

## Issue 1: InvalidAMIID.NotFound

**Error:**


**Cause:**
The `run-instances` command had a hardcoded region `us-east-1`, while the AMI was dynamically fetched for `us-west-2`. AMI IDs are region-specific — an AMI from one region does not exist in another.

**Fix:**
Changed the hardcoded region in the script:
```bash
--region us-east-1 \    #  Wrong
--region $region \      #  Correct
