Logging Level Best Practice

I've seen a few types of error logging frameworks, but commonly they provide five different levels:

- Error
- Warn
- Info
- Debug
- Trace

Such as [Rust log](https://doc.rust-lang.org/log/log/enum.LogLevel.html).

GStreamer comes at more [levels](https://gstreamer.freedesktop.org/data/doc/gstreamer/head/gstreamer/html/gst-running.html) (choose from 0 to 9): 

- 1 - ERROR: Logs all fatal errors
- 2 - WARNING: Logs all warnings. Typically these are non-fatal, but user-visible problems are expected to happen.
- 3 - FXIME: Logs all fixme messages. Fixme messages are messages that indicate that something in the executed code path is not fully implemented or handled yet. The purpose of this message is to make it easier to spot incomplete/unfinished pieces of code when reading the debug log.
- 4 - Logs all informational messages. These are typically used for events in the system that only happen once, or are important and rare enough to be logged at this level.
- 5 - Debug: Logs all debug messages. These are general debug messages for events that happen only a limited number of times during an object's lifetime; these include setup, teardown, change of parameters, ...
- 6 - Logs all log messages. These are messages for events that happen repeatedly during an object's lifetime; these include streaming and steady-state conditions.
- 7 - Logs all trace messages. These messages for events that happen repeatedly during an object's lifetime such as the ref/unref cycles.
- 9 - Log all memory dump messages. Memory dump messages are used to log (small) chunks of data as memory dumps in the log. They will be displayed as hexdump with ASCII characters.

glog 
INFO, WARNING, ERROR, and FATAL
and a somewhat useful The DFATAL severity logs a FATAL error in debug mode (i.e., there is no NDEBUG macro defined), but avoids halting the program in production by automatically reducing the severity to ERROR.


I generally subscribe to the following convention:

Trace - Only when I would be "tracing" the code and trying to find one part of a function specifically.
Debug - Information that is diagnostically helpful to people more than just developers (IT, sysadmins, etc.).
Info - Generally useful information to log (service start/stop, configuration assumptions, etc). Info I want to always have available but usually don't care about under normal circumstances. This is my out-of-the-box config level.
Warn - Anything that can potentially cause application oddities, but for which I am automatically recovering. (Such as switching from a primary to backup server, retrying an operation, missing secondary data, etc.)
Error - Any error which is fatal to the operation, but not the service or application (can't open a required file, missing data, etc.). These errors will force user (administrator, or direct user) intervention. These are usually reserved (in my apps) for incorrect connection strings, missing services, etc.
Fatal - Any error that is forcing a shutdown of the service or application to prevent data loss (or further data loss). I reserve these only for the most heinous errors and situations where there is guaranteed to have been data corruption or loss.

Android has 6.
int	ASSERT
Priority constant for the println method.
int	DEBUG
Priority constant for the println method; use Log.d.
int	ERROR
Priority constant for the println method; use Log.e.
int	INFO
Priority constant for the println method; use Log.i.
int	VERBOSE
Priority constant for the println method; use Log.v.
int	WARN
Priority constant for the println method; use Log.w.
