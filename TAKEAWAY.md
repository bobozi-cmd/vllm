# EngineCoreClient
- EngineCoreClient::make_client 三种client实现:
    | multiprocess | asyncio | 实现            | 用途                                     |
    |--------------|---------|---------------|----------------------------------------|
    | False        | False   | InprocClient  | 同进程, 调试/简单场景                           |
    | True         | False   | SyncMPClient  | 同步 + 独立进程(`LLM` 离线批处理)                 |
    | True         | True    | AsyncMPClient | 异步 + 独立进程(`AsyncLLM` ,即 OpenAI server) |
    - 上层`LLMEngine` 完全不知道核心是在同进程还是隔进程,只调`add_request` /`get_output` 这套统一接口
