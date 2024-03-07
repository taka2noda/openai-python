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
$ sudo more /etc/datadog-agent/datadog.yaml | grep -n "# process_config"
$ sed -i 's/# dogstatsd_stats_enable: false/dogstatsd_stats_enable: true/g' /etc/datadog-agent/datadog.yaml
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
![Screenshot 2024-03-07 at 23 51 35](https://github.com/taka2noda/openai-python/assets/93112551/018d5118-4702-4a91-8dc8-e1ac8cd1f1d3)
![Screenshot 2024-03-07 at 23 52 15](https://github.com/taka2noda/openai-python/assets/93112551/435afdf8-f0ef-42f4-bc61-2b26766ff9a7)
![Screenshot 2024-03-07 at 23 52 56](https://github.com/taka2noda/openai-python/assets/93112551/46a49f1d-3591-4c04-93bc-54d8b3f95b6d)
![Screenshot 2024-03-07 at 0 28 26](https://github.com/taka2noda/openai-python/assets/93112551/785938fa-b04b-415a-9865-a9e247f91331)
![Screenshot 2024-03-07 at 0 28 45](https://github.com/taka2noda/openai-python/assets/93112551/9f723a2d-f14e-4585-a2ba-5bbf5181a31c)
![Screenshot 2024-03-07 at 23 27 47](https://github.com/taka2noda/openai-python/assets/93112551/78f83906-4e1c-4375-8837-ef19770dc347)
![Screenshot 2024-03-07 at 23 27 27](https://github.com/taka2noda/openai-python/assets/93112551/20d7a823-73ba-4f71-84a1-1bf2b484ac8e)
![Screenshot 2024-03-07 at 23 27 16](https://github.com/taka2noda/openai-python/assets/93112551/3eddb80a-c92e-455b-82c9-6e5aa8b42fe3)
![Screenshot 2024-03-06 at 22 10 58](https://github.com/taka2noda/openai-python/assets/93112551/b57efb4f-eb23-4536-8ef7-924afa3a081b)









