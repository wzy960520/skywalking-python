## Change Logs

### 1.0.0 
- Feature:

- Plugins:
  - Add Psycopg(3.x) support (In-progress)

- Fixes:

- Others:
  - Add support for Python 3.10

### 0.7.0

- Feature:
    - Support collecting and reporting logs to backend (#147)
    - Support profiling Python method level performance (#127
    - Add a new `sw-python` CLI that enables agent non-intrusive integration (#156)
    - Add exponential reconnection backoff strategy when OAP is down (#157)
    - Support ignoring traces by http method (#143)
    - `NoopSpan` on queue full, propagation downstream (#141)
    - Support agent namespace. (#126)
    - Support secure connection option for GRPC and HTTP (#134)

- Plugins:
    - Add Falcon Plugin (#146)
    - Update `sw_pymongo.py` to be compatible with cluster mode (#150)
    - Add Python celery plugin (#125)
    - Support tornado5+ and tornado6+ (#119)

- Fixes:
    - Remove HTTP basic auth credentials from log, stacktrace, segment (#152)
    - Fix `@trace` decorator not work (#136)
    - Fix grpc disconnect, add `SW_AGENT_MAX_BUFFER_SIZE` to control buffer queue size (#138)

- Others:
    - Chore: bump up `requests` version to avoid license issue (#142)
    - Fix module wrapt as normal install dependency (#123)
    - Explicit component inheritance (#132)
    - Provide dockerfile & images for easy integration in containerized scenarios (#159)
 
### 0.6.0

- Fixes:
    - Segment data loss when gRPC timing out. (#116)
    - `sw_tornado` plugin async handler status set correctly. (#115)
    - `sw_pymysql` error when connection haven't db. (#113)

### 0.5.0

- New plugins
    - Pyramid Plugin (#102)
    - AioHttp Plugin (#101)
    - Sanic Plugin (#91)

- API and enhancements
    - `@trace` decorator supports `async` functions
    - Supports async task context
    - Optimized path trace ignore
    - Moved exception check to `Span.__exit__`
    - Moved Method & Url tags before requests

- Fixes:
    - `BaseExceptions` not recorded as errors
    - Allow pending data to send before exit
    - `sw_flask` general exceptions handled
    - Make `skywalking` logging Non-global

- Chores and tests
    - Make tests really run on specified Python version
    - Deprecate 3.5 as it's EOL

### 0.4.0

- Feature: Support Kafka reporter protocol (#74)
- BugFix: Move generated packages into `skywalking` namespace to avoid conflicts (#72)
- BugFix: Agent cannot reconnect after server is down (#79)
- Test: Mitigate unsafe yaml loading (#76)

### 0.3.0

- New plugins
    - Urllib3 Plugin (#69)
    - Elasticsearch  Plugin (#64)
    - PyMongo Plugin (#60)
    - Rabbitmq Plugin (#53)
    - Make plugin compatible with Django (#52)
    
- API
    - Add process propagation (#67)
    - Add tags to decorators (#65)
    - Add Check version of packages when install plugins (#63)
    - Add thread propagation (#62)
    - Add trace ignore (#59)
    - Support snapshot context (#56)
    - Support correlation context (#55)
    
- Chores and tests
    - Test: run multiple versions of supported libraries (#66)
    - Chore: add pull request template for plugin (#61)
    - Chore: add dev doc and reorganize the structure (#58)
    - Test: update test health check (#57)
    - Chore: add make goal to package release tar ball (#54)
    
    
    
### 0.2.0

- New plugins
    - Kafka Plugin (#50)
    - Tornado Plugin (#48)
    - Redis Plugin (#44)
    - Django Plugin (#37)
    - PyMsql Plugin (#35)
    - Flask plugin (#31)

- API
    - Add ignore_suffix Config (#40)
    - Add missing `log` method and simplify test codes (#34)
    - Add content equality of SegmentRef (#30)
    - Validate carrier before using it (#29)

- Chores and tests
    - Test: print the diff list when validation failed (#46)
    - Created venv builders for linux/windows and req flashers + use documentation (#38)

### 0.1.0

- API: agent core APIs, check [the APIs and the examples](https://github.com/apache/skywalking-python/blob/3892cab9d5d2c03107cfb2b1c59a6c77c5c3cc35/README.md#api)
- Plugin: built-in libraries `http`, `urllib.request` and third-party library `requests` are supported.
- Test: agent test framework is setup, and the corresponding tests of aforementioned plugins are also added.
