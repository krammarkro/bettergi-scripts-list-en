- Routes in this directory do not overlap with those in `Medium Efficiency`. Users can run only high-efficiency routes or all routes according to their needs.

- Some routes require Nahida, but can also run without her. BetterGI will automatically skip routes that require her if unavailable.

- For developers: The threshold separating high and medium efficiency is 5.0 Bird Eggs per minute. Calculated as: $`\frac{Expected Yield}{Runtime + Script Delay}`$，where script delay is 1 second after version 0.55.
