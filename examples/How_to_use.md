# How to use

## Datadog Docs
- OpenAI Account Integration: https://docs.datadoghq.com/integrations/openai/?tab=apikey
  
  Start here first. Just follow the guide.
  
- Python Application Trace: https://docs.datadoghq.com/integrations/openai/?tab=python
  
  This document's topic.
  
## Example OpenAI Application (Here)
- Forked from official example and changed model to make it cheaper and cause error.

  https://github.com/taka2noda/openai-python/tree/main/examples

## Tested on 
- EC2(Ubuntu 22.04.3 LTS (GNU/Linux 6.2.0-1017-aws x86_64))

## Commands
Install Datadog Agent.

```
$ DD_API_KEY="YOUR_DATADOGAPI_KEY" DD_SITE="datadoghq.com"  bash -c "$(curl -L https://s3.amazonaws.com/dd-agent/scripts/install_script_agent7.sh)"
```

Install python and openai library.
```
$ sudo apt update
$ sudo apt install python3
$ sudo apt install python3-pip
$ pip install openai
```
Enable StatsD in your Datadog Agent.
```
$ sed -i 's/# dogstatsd_stats_enable: false/dogstatsd_stats_enable: true/g' datadog.yaml
$ sudo service datadog-agent restart
$ sudo datadog-agent status
```
Install the Datadog APM Python library.
```
$ pip install ddtrace
```
Clone Sample Application Repo.
```
$ git clone https://github.com/taka2noda/openai-python.git
```
Define environment variables.
```
$ export OPENAI_API_KEY="YOUR_OPENAPI_KEY"
$ export DD_API_KEY="YOUR_DATADOGAPI_KEY"
$ cd openai-python/examples
```
Execute 1. Simple
```
$ DD_SERVICE="taka2-openai-demo" DD_ENV="dev" DD_OPENAI_LOGS_ENABLED="true" DD_OPENAI_LOG_PROMPT_COMPLETION_SAMPLE_RATE="1.0" ddtrace-run python3 demo-gpt-35.py
```
Execute 2. Error
```
$ DD_SERVICE="taka2-openai-demo" DD_ENV="dev" DD_OPENAI_LOGS_ENABLED="true" DD_OPENAI_LOG_PROMPT_COMPLETION_SAMPLE_RATE="1.0" ddtrace-run python3 demo-error.py
```
Execute 3. Call Dall-e model
```
$ DD_SERVICE="taka2-openai-picture" DD_ENV="dev" DD_OPENAI_LOGS_ENABLED="true" DD_OPENAI_LOG_PROMPT_COMPLETION_SAMPLE_RATE="1.0" ddtrace-run python3 picture.py
```
No use others because expensive

## Outcome
![Screenshot 2024-03-06 at 22 37 55](https://github.com/taka2noda/openai-python/assets/93112551/dcdd4d18-2a3d-40a0-948e-98331f1ac601)
![Screenshot 2024-03-06 at 22 10 30](https://github.com/taka2noda/openai-python/assets/93112551/405b76b4-bd9c-48ea-aa43-82fe32bab3f3)
![Screenshot 2024-03-06 at 22 10 39](https://github.com/taka2noda/openai-python/assets/93112551/c4d74e20-19cc-4afe-b705-637aec775e41)
![Screenshot 2024-03-06 at 22 10 58](https://github.com/taka2noda/openai-python/assets/93112551/f1c654ef-c123-486f-93e4-855ab1f3e55e)




