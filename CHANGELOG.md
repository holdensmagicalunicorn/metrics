v2.0.0-BETA16: Aug 23 2011
==========================

* Fixed a bug in GC monitoring.


v2.0.0-BETA15: Aug 15 2011
==========================

* Fixed dependency scopes for `metrics-jetty`.
* Added time and VM version to `vm` output of `MetricsServlet`.
* Dropped `com.sun.mangement`-based GC instrumentation in favor of a
  `java.lang.management`-based one. `getLastGcInfo` has a nasty native memory
  leak in it, plus it often returned incorrect data.
* Upgraded to Jackson 1.8.5.
* Upgraded to Jetty 7.4.5.
* Added sanitization for metric names in `GraphiteReporter`.
* Extracted out a `Clock` interface for timers for non-wall-clock timing.
* Extracted out most of the remaining statics into `MetricsRegistry` and
  `HealthCheckRegistry`.
* Added an init parameter to `MetricsServlet` for disabling the `jvm` section.
* Added a Guice module for `MetricsServlet`.
* Added dynamic metric names.
* Upgraded to ehcache 2.4.5.
* Upgraded to logback 0.9.29.
* Allowed for the removal of metrics.
* Added the ability to filter metrics exposed by a reporter to those which match
  a given predicate.


v2.0.0-BETA14: Jul 05 2011
==========================

* Moved to Maven for a build system and extracted the Scala façade to a
  `metrics-scala` module which is now the only cross-built module. All other
  modules dropped the Scala version suffix in their `artifactId`s.
* Fixed non-heap metric name in `GraphiteReporter`.
* Fixed stability error in `GraphiteReporter` when dealing with unavilable
  servers.
* Fixed error with anonymous, instrumented classes.
* Fixed error in `MetricsServlet` when a gauge throws an exception.
* Fixed error with bogus GC run times.
* Link to the pretty JSON output from the `MetricsServlet` menu page.
* Fixed potential race condition in histograms' variance calculations.
* Fixed memory pool reporting for the G1 collector.


v2.0.0-BETA13: May 13 2011
==========================

* Fixed a bug in the intial startup phase of the `JmxReporter`.
* Added `metrics-ehcache`, for the instrumentation of `Ehcache` instances.
* Fixed a typo in `metrics-jetty`'s `InstrumentedHandler`.
* Added name prefixes to `GraphiteReporter`.
* Added JVM metrics reporting to `GraphiteReporter`.
* Actually fixed `MetricsServlet`'s links when the servlet has a non-root
  context path.
* Now cross-building for Scala 2.9.0.
* Added `pretty` query parameter for `MetricsServlet` to format the JSON object
  for human consumption.
* Added `no-cache` headers to the `MetricsServlet` responses.


v2.0.0-BETA12: May 09 2011
==========================

* Upgraded to Jackson 1.7.6.
* Added a new instrumented Log4J appender.
* Added a new instrumented Logback appender. Thanks to Bruce Mitchener
  (@waywardmonkeys) for the patch.
* Added a new reporter for the [Graphite](http://graphite.wikidot.com)
  aggregation system. Thanks to Mahesh Tiyyagura (@tmahesh) for the patch.
* Added scoped metric names.
* Added Scala 2.9.0.RC{2,3,4} as build targets.
* Added meters to Jetty handler for the percent of responses which have `4xx` or
  `5xx` status codes.
* Changed the Servlet API to be a `provided` dependency. Thanks to Mårten
  Gustafson (@chids) for the patch.
* Separated project into modules:
  * `metrics-core`: A dependency-less project with all the core metrics.
  * `metrics-graphite`: A reporter for the [Graphite](http://graphite.wikidot.com)
    aggregation system.
  * `metrics-guice`: Guice AOP support.
  * `metrics-jetty`: An instrumented Jetty handler.
  * `metrics-log4j`: An instrumented Log4J appender.
  * `metrics-logback`: An instrumented Logback appender.
  * `metrics-servlet`: The Metrics servlet with context listener.


v2.0.0-BETA11: Apr 27 2011
==========================

* Added thread state and deadlock detection metrics.
* Fix `VirtualMachineMetrics`' initialization.
* Context path fixes for the servlet.
* Added the `@Gauge` annotation.
* Big reworking of the exponentially-weighted moving average code for meters.
  Thanks to JD Maturen (@sku) and John Ewart (@johnewart) for pointing this out.
* Upgraded to Guice 3.0.
* Upgraded to Jackson 1.7.5.
* Upgraded to Jetty 7.4.0.
* Big rewrite of the servlet's thread dump code.
* Fixed race condition in `ExponentiallyDecayingSample`. Thanks to Martin
  Traverso (@martint) for the patch.
* Lots of spelling fixes in Javadocs. Thanks to Bruce Mitchener
  (@waywardmonkeys) for the patch.
* Added Scala 2.9.0.RC1 as a build target. Thanks to Bruce Mitchener
  (@waywardmonkeys) for the patch.
* Patched a hilarious memory leak in `java.util.logging`.


v2.0.0-BETA10: Mar 25 2011
==========================

* Added Guice AOP annotations.
* Added `HealthCheck#name()`.
* Added `Metrics.newJmxGauge()`.
* Moved health checks into `HealthChecks`.
* Upgraded to Jackon 1.7.3 and Jetty 7.3.1.

v2.0.0-BETA10: Mar 25 2011
==========================

* Added Guice AOP annotations: `@Timed` and `@Metered`.
* Added `HealthCheck#name()`.
* Added `Metrics.newJmxGauge()`.
* Moved health checks into `HealthChecks`.
* Upgraded to Jackon 1.7.3 and Jetty 7.3.1.

v2.0.0-BETA9: Mar 14 2011
=========================

* Fixed `JmxReporter` lag.
* Added default arguments to timers and meters.
* Added default landing page to the servlet.
* Improved the performance of `ExponentiallyDecayingSample`.
* Fixed an integer overflow bug in `UniformSample`.
* Added linear scaling to `ExponentiallyDecayingSample`.

v2.0.0-BETA8: Mar 01 2011
=========================

* Added histograms.
* Added biased sampling for timers.
* Added dumping of timer/histogram samples via the servlet.
* Added dependency on `jackon-mapper`.
* Added classname filtering for the servlet.
* Added URI configuration for the servlet.


v2.0.0-BETA7: Jan 12 2011
=========================

* Added `JettyHandler`.
* Made the `Servlet` dependency optional.

v2.0.0-BETA6: Jan 12 2011
=========================

* Fix `JmxReporter` initialization.

v2.0.0-BETA5: Jan 11 2011
=========================

* Dropped `Counter#++` and `Counter#--`.
* Added `Timer#update`.
* Upgraded to Jackson 1.7.0.
* Made JMX reporting implicit.
* Added health checks.

v2.0.0-BETA3: Dec 23 2010
=========================

* Fixed thread names and some docs.

v2.0.0-BETA2: Dec 22 2010
=========================

* Fixed a memory leak in `MeterMetric`.

v2.0.0-BETA1: Dec 22 2010
=========================

* Total rewrite in Java.

v1.0.7: Sep 21 2010
===================

* Added `median` to `Timer`.
* Added `p95` to `Timer` (95th percentile).
* Added `p98` to `Timer` (98th percentile).
* Added `p99` to `Timer` (99th percentile).

v1.0.6: Jul 15 2010
===================

* Now compiled exclusively for 2.8.0 final.

v1.0.5: Jun 01 2010
===================

* Documentation fix.
* Added `TimedToggle`, which may or may not be useful at all.
* Now cross-building for RC2 and RC3.

v1.0.4: Apr 27 2010
===================

* Blank `Timer`s (i.e., those which have recorded no timings yet) no longer
  explode when asked for metrics for that which does not yet exist.
* Nested classes, companion objects, and singletons don't have trailing `$`s
  messing up JMX's good looks.

v1.0.3: Apr 16 2010
===================

* Fixed some issues with the [implicit.ly](http://implicit.ly) plumbing.
* Tweaked the sample size for `Timer`, giving it 99.9% confidence level with a
  %5 margin of error (for a normally distributed variable, which it almost
  certainly isn't.)
* `Sample#iterator` returns only the recorded data, not a bunch of zeros.
* Moved units of `Timer`, `Meter`, and `LoadMeter` to their own attributes,
  which allows for easy export of Metrics data via JMX to things like
  [Ganglia](http://ganglia.sourceforge.net/) or whatever.

v1.0.2: Mar 08 2010
===================

* `Timer` now uses Welford's algorithm for calculating running variance, which
  means no more hilariously wrong standard deviations (e.g., `NaN`).
* `Timer` now supports `+=(Long)` for pre-recorded, nanosecond-precision
  timings.

v1.0.1: Mar 05 2010
===================

* changed `Sample` to use an `AtomicReferenceArray`

v1.0.0: Feb 27 2010
===================

* Initial release
