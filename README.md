# performance-logger

> Learning project, 2017. Not maintained — archived for reference.

Method-timing for Java: annotate a method with `@PerformanceLog` and its execution time,
signature, and arguments are logged. Two integration paths share one implementation.

## Design

- **`@PerformanceLog`** — runtime annotation, targets types or methods.
- **`PerformanceLogAspect`** — AspectJ `@Around` advice for annotation-driven weaving.
- **`PerformanceLogInterceptor`** — an AOP-Alliance `MethodInterceptor` for Spring-style
  proxy interception.
- Both delegate to **`PerformanceLogger`**, which wraps a Guava `Stopwatch` around a
  `Loggable` — an abstraction over either a `ProceedingJoinPoint` (`JoinPointLogger`) or a
  `MethodInvocation` (`MethodLogger`), so the timing/logging logic exists once.

Java 8 · AspectJ · AOP-Alliance · Guava · SLF4J · Gradle

Extracted from a work codebase as a study of AOP; the aspect pointcut still references the
original project's annotation package.
