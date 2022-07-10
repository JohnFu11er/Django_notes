# Setting up an AWS Linux EC2 instance for Django with Postgresql

### Install EPEL using Amazon's special installer
```bash
sudo amazon-linux-extras install epel
sudo yum install libpqxx-devel
```

### Create virtual environment
```
python3 -m venv <name of environment>
```

### Activate virtual environment
```
source <path to 'activate' script>
```

### Install postgresql and supporting packages
```bash
sudo yum install postgresql postgresql-contrib python3-devel
```

### Install required software and packages
```bash
pip3 install django
pip3 install psycopg2
```
