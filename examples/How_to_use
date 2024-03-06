## How to use

# Guide
https://docs.datadoghq.com/integrations/openai/?tab=python 

# Example Application (Here)
https://github.com/taka2noda/openai-python/tree/main/examples

# Tested on EC2(Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1017-aws x86_64))

# Commands
Install Datadog Agent.
$ DD_API_KEY="YOUR_DATADOGAPI_KEY" DD_SITE="datadoghq.com"  bash -c "$(curl -L https://s3.amazonaws.com/dd-agent/scripts/install_script_agent7.sh)"

Install python and openai library.
$ sudo apt update
$ sudo apt install python3
$ sudo apt install python3-pip
$ pip install openai

Enable StatsD in your Datadog Agent.
$ sed -i 's/# dogstatsd_stats_enable: false/dogstatsd_stats_enable: true/g' datadog.yaml
$ sudo service datadog-agent restart
$ sudo datadog-agent status
$ sudo more /etc/datadog-agent/datadog.yaml | grep -n "# process_config"

Install the Datadog APM Python library.
$ pip install ddtrace

Clone Sample Application Repo
$ git clone https://github.com/taka2noda/openai-python.git

Excute
$ cd /openai-python/examples
$ export OPENAI_API_KEY="YOUR_OPENAPI_KEY"
$ export DD_API_KEY="YOUR_DATADOGAPI_KEY"
$ cd openai-python/examples
$ DD_SERVICE="taka2-openai-demo" DD_ENV="dev" DD_OPENAI_LOGS_ENABLED="true" DD_OPENAI_LOG_PROMPT_COMPLETION_SAMPLE_RATE="1.0" ddtrace-run python3 demo-gpt-35.py
error
$ DD_SERVICE="taka2-openai-demo" DD_ENV="dev" DD_OPENAI_LOGS_ENABLED="true" DD_OPENAI_LOG_PROMPT_COMPLETION_SAMPLE_RATE="1.0" ddtrace-run python3 demo-error.py
Call Dall-e model
$ DD_SERVICE="taka2-openai-picture" DD_ENV="dev" DD_OPENAI_LOGS_ENABLED="true" DD_OPENAI_LOG_PROMPT_COMPLETION_SAMPLE_RATE="1.0" ddtrace-run python3 picture.py
No use others because expensive
