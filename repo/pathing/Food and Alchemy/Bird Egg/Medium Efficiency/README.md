- 本目录下的Route与`High Efficiency`目录下的Route互不重合，用户可根据自己的实际需求选择仅跑Efficient Route或全都跑。

- Some routes require Nahida, but can also run without her. BetterGI will automatically skip routes that require her if unavailable.

- For developers: The threshold separating high and medium efficiency is 5.0 Bird Eggs per minute. Calculated as: $`\frac{Expected Yield}{Runtime + Script Delay}`$，where script delay is 1 second after version 0.55.
