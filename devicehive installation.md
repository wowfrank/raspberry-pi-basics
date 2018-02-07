### install PostgreSQL on xUbuntu

1. Open Terminal
1. Setup Apt Repo File
   ```bash
   sudo echo "deb http://apt.postgresql.org/pub/repos/apt/ zesty-pgdg main" \
   /etc/apt/sources.list.d/pgdg.list
   ```
1. Import GPG Key
   ```bash
   wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | \
   sudo apt-key add -
   ```
1. Refesh Apt Repositories
   ```bash
   sudo apt update
   ```
1. Install PostgreSQL for Xubuntu
   ```bash
   sudo apt install postgresql-10
   ```
   
### Install Apache Kafka

Following instructions listed in [kafka Quickstart](https://kafka.apache.org/quickstart#quickstart_startserver)
