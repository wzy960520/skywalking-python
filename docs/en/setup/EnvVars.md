# Supported Environment Variables

Below is the full list of supported environment variables you can set to 
customize the agent behavior, please read the descriptions for what they can achieve.

Environment Variable | Description | Default
| :--- | :--- | :--- |
| `SW_AGENT_NAME` | The name of the Python service | `Python Service Name` |
| `SW_AGENT_INSTANCE` | The name of the Python service instance | Randomly generated |
| `SW_AGENT_NAMESPACE` | The agent namespace of the Python service | unset |
| `SW_AGENT_COLLECTOR_BACKEND_SERVICES` | The backend OAP server address | `127.0.0.1:11800` |
| `SW_AGENT_FORCE_TLS` | Use TLS for communication with server (no cert required) | `False` |
| `SW_AGENT_PROTOCOL` | The protocol to communicate with the backend OAP, `http`, `grpc` or `kafka`, **we highly suggest using `grpc` in production as it's well optimized than `http`**. The `kafka` protocol provides an alternative way to submit data to the backend. | `grpc` |
| `SW_AGENT_AUTHENTICATION` | The authentication token to verify that the agent is trusted by the backend OAP, as for how to configure the backend, refer to [the yaml](https://github.com/apache/skywalking/blob/4f0f39ffccdc9b41049903cc540b8904f7c9728e/oap-server/server-bootstrap/src/main/resources/application.yml#L155-L158). | unset |
| `SW_AGENT_LOGGING_LEVEL` | The logging level, could be one of `CRITICAL`, `FATAL`, `ERROR`, `WARN`(`WARNING`), `INFO`, `DEBUG` | `INFO` |
| `SW_AGENT_DISABLE_PLUGINS` | The name patterns in CSV pattern, plugins whose name matches one of the pattern won't be installed | `''` |
| `SW_AGENT_MAX_BUFFER_SIZE` | The maximum queue backlog size for sending the segment data to backend, segments beyond this are silently dropped | `'10000'` |
| `SW_HTTP_IGNORE_METHOD` | Comma-delimited list of http methods to ignore (GET, POST, HEAD, OPTIONS, etc...) | `` |
| `SW_SQL_PARAMETERS_LENGTH` | The maximum length of the collected parameter, parameters longer than the specified length will be truncated, length 0 turns off parameter tracing | `0` |
| `SW_PYMONGO_TRACE_PARAMETERS` | Indicates whether to collect the filters of pymongo | `False` |
| `SW_PYMONGO_PARAMETERS_MAX_LENGTH` | The maximum length of the collected filters, filters longer than the specified length will be truncated |  `512` |
| `SW_IGNORE_SUFFIX` | If the operation name of the first span is included in this set, this segment should be ignored. | `.jpg,.jpeg,.js,.css,.png,.bmp,.gif,.ico,.mp3,.mp4,.html,.svg` |
| `SW_FLASK_COLLECT_HTTP_PARAMS`| This config item controls that whether the Flask plugin should collect the parameters of the request.| `false` |
| `SW_DJANGO_COLLECT_HTTP_PARAMS`| This config item controls that whether the Django plugin should collect the parameters of the request.| `false` |
| `SW_HTTP_PARAMS_LENGTH_THRESHOLD`| When `COLLECT_HTTP_PARAMS` is enabled, how many characters to keep and send to the OAP backend, use negative values to keep and send the complete parameters, NB. this config item is added for the sake of performance.  | `1024` |
| `SW_CORRELATION_ELEMENT_MAX_NUMBER`|Max element count of the correlation context.| `3` |
| `SW_CORRELATION_VALUE_MAX_LENGTH`| Max value length of correlation context element.| `128` |
| `SW_TRACE_IGNORE`| This config item controls that whether the trace should be ignore | `false` |
| `SW_TRACE_IGNORE_PATH`| You can setup multiple URL path patterns, The endpoints match these patterns wouldn't be traced. the current matching rules follow Ant Path match style , like /path/*, /path/**, /path/?.| `''` |
| `SW_ELASTICSEARCH_TRACE_DSL`| If true, trace all the DSL(Domain Specific Language) in ElasticSearch access, default is false | `false` |
| `SW_KAFKA_REPORTER_BOOTSTRAP_SERVERS` | A list of host/port pairs to use for establishing the initial connection to the Kafka cluster. It is in the form host1:port1,host2:port2,... | `localhost:9092` |
| `SW_KAFKA_REPORTER_TOPIC_MANAGEMENT` | Specifying Kafka topic name for service instance reporting and registering. | `skywalking-managements` |
| `SW_KAFKA_REPORTER_TOPIC_SEGMENT` | Specifying Kafka topic name for Tracing data. | `skywalking-segments` |
| `SW_KAFKA_REPORTER_TOPIC_LOG` | Specifying Kafka topic name for Log data. | `skywalking-logs` |
| `SW_KAFKA_REPORTER_CONFIG_key` | The configs to init KafkaProducer. it support the basic arguments (whose type is either `str`, `bool`, or `int`) listed [here](https://kafka-python.readthedocs.io/en/master/apidoc/KafkaProducer.html#kafka.KafkaProducer) | unset |
| `SW_CELERY_PARAMETERS_LENGTH`| The maximum length of `celery` functions parameters, longer than this will be truncated, 0 turns off  | `512` |
| `SW_AGENT_PROFILE_ACTIVE` | If `True`, Python agent will enable profile when user create a new profile task. Otherwise disable profile. | `True` |
| `SW_PROFILE_TASK_QUERY_INTERVAL` | The number of seconds between two profile task query. | `20` |
| `SW_AGENT_PROFILE_MAX_PARALLEL` | The number of parallel monitor segment count. | `5` |
| `SW_AGENT_PROFILE_DURATION` | The maximum monitor segment time(minutes), if current segment monitor time out of limit, then stop it. | `10` |
| `SW_AGENT_PROFILE_DUMP_MAX_STACK_DEPTH` | The number of max dump thread stack depth | `500` |
| `SW_AGENT_PROFILE_SNAPSHOT_TRANSPORT_BUFFER_SIZE` | The number of snapshot transport to backend buffer size | `50` |
| `SW_AGENT_LOG_REPORTER_ACTIVE` | If `True`, Python agent will report collected logs to the OAP or Satellite. Otherwise, it disables the feature. | `False` |
| `SW_AGENT_LOG_REPORTER_BUFFER_SIZE` | The maximum queue backlog size for sending log data to backend, logs beyond this are silently dropped. | `10000` |
| `SW_AGENT_LOG_REPORTER_LEVEL` | This config specifies the logger levels of concern, any logs with a level below the config will be ignored. | `WARNING` |
| `SW_AGENT_LOG_REPORTER_IGNORE_FILTER` | This config customizes whether to ignore the application-defined logger filters, if `True`, all logs are reported disregarding any filter rules. | `False` |
| `SW_AGENT_LOG_REPORTER_FORMATTED` | If `True`, the log reporter will transmit the logs as formatted. Otherwise, puts logRecord.msg and logRecord.args into message content and tags(`argument.n`), respectively. Along with an `exception` tag if an exception was raised. | `True` |
| `SW_AGENT_LOG_REPORTER_LAYOUT` | The log reporter formats the logRecord message based on the layout given. | `%(asctime)s [%(threadName)s] %(levelname)s %(name)s - %(message)s` |
| `SW_AGENT_CAUSE_EXCEPTION_DEPTH` | This config limits agent to report up to `limit` stacktrace, please refer to [Python traceback](https://docs.python.org/3/library/traceback.html#traceback.print_tb) for more explanations. | `5` | 
| `SW_PYTHON_BOOTSTRAP_PROPAGATE`| This config controls the child process agent bootstrap behavior in `sw-python` CLI, if set to `False`, a valid child process will not boot up a SkyWalking Agent. Please refer to the [CLI Guide](CLI.md) for details. | unset |
| `SW_FASTAPI_COLLECT_HTTP_PARAMS`| This config item controls that whether the FastApi plugin should collect the parameters of the request.| `false` |
