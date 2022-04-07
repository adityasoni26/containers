# Minimal Container

**Disclaimer** This image is not regularly patched for security updates. It is the user's responsibility to regularly patch and rebuild the images. If this is a concern, please set automation to regularly rebuild your DCS base images

**Note:** This image specifically for Databricks Runtime 7.x and above; see the [latest runtime releases](https://docs.databricks.com/release-notes/runtime/releases.html#databricks-runtime-releases) for reference. 

This image is the smallest example of what is necessary to launch a cluster in Databricks.
This is intended for users who know exactly what they need and do not need.

## Supported Features
  - Scala Notebooks
  - Java/Jar jobs

## Unsupported Features
  - Python Notebooks, Python Jobs
  - Spark Submit Jobs
  - %sh
  - DBFS FUSE mount (/dbfs)
  - SSH
  - Ganglia
