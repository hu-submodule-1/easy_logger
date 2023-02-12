## easy_logger

### 介绍

从[EasyLogger](https://github.com/armink/EasyLogger)适配到Linux平台的日志库

### 使用说明

- 说明文档: 详见[EasyLogger 核心功能移植说明](https://github.com/armink/EasyLogger/blob/master/docs/zh/port/kernel.md)中`设置参数`
- 示例代码: [easy_logger_demo](https://github.com/hu-submodule-demo/easy_logger_demo)
- 初始化参考代码
    ```c
    /**
     * @brief  初始化easy_logger
     */
    static void easy_logger_init(void)
    {
        /* close printf buffer */
        setbuf(stdout, NULL);
        /* initialize EasyLogger */
        elog_init();
        /* set EasyLogger log format */
        elog_set_fmt(ELOG_LVL_ASSERT, ELOG_FMT_ALL);
        elog_set_fmt(ELOG_LVL_ERROR, (ELOG_FMT_ALL & ~(ELOG_FMT_P_INFO | ELOG_FMT_T_INFO)));
        elog_set_fmt(ELOG_LVL_WARN, (ELOG_FMT_ALL & ~(ELOG_FMT_P_INFO | ELOG_FMT_T_INFO)));
        elog_set_fmt(ELOG_LVL_INFO, (ELOG_FMT_ALL & ~(ELOG_FMT_P_INFO | ELOG_FMT_T_INFO)));
        elog_set_fmt(ELOG_LVL_DEBUG, (ELOG_FMT_ALL & ~(ELOG_FMT_P_INFO | ELOG_FMT_T_INFO)));
        elog_set_fmt(ELOG_LVL_VERBOSE, (ELOG_FMT_ALL & ~(ELOG_FMT_P_INFO | ELOG_FMT_T_INFO)));
    #ifdef ELOG_COLOR_ENABLE
        elog_set_text_color_enabled(true);
    #endif
        /* start EasyLogger */
        elog_start();
    }
    ```
