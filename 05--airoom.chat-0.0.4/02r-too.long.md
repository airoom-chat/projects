
BadRequestError: 400 This model's maximum context length is 4097 tokens. However, your messages resulted in 4945 tokens. Please reduce the length of the messages.                                                                          at Function.generate (/home/ubuntu/packdir/node_modules/openai/src/error.ts:56:14)                                      at OpenAI.makeStatusError (/home/ubuntu/packdir/node_modules/openai/src/core.ts:348:21)                                 at OpenAI.makeRequest (/home/ubuntu/packdir/node_modules/openai/src/core.ts:406:24)                                     at processTicksAndRejections (node:internal/process/task_queues:95:5)                                                   at MessageAnonymousController.sendMessage (/home/ubuntu/packdir/src/airoomanonymous/message.controller.ts:122:26)       at /home/ubuntu/packdir/node_modules/@nestjs/core/router/router-execution-context.js:46:28                              at /home/ubuntu/packdir/node_modules/@nestjs/core/router/router-proxy.js:9:17 {
  status: 400,
  headers: {
    'access-control-allow-origin': '*',
    'alt-svc': 'h3=":443"; ma=86400',
    'cf-cache-status': 'DYNAMIC',
    'cf-ray': '822dccaf4f83c3a3-SEA',
    connection: 'keep-alive',
    'content-length': '281',
    'content-type': 'application/json',
    date: 'Wed, 08 Nov 2023 12:25:36 GMT',
    'openai-organization': 'user-ccx7fjkx7sklzsezi5sc4sa6',
    'openai-processing-ms': '24',
    'openai-version': '2020-10-01',
    server: 'cloudflare',
    'set-cookie': '__cf_bm=30Ah57Yl8MJjYYP0rb4xlp9mazYHruNoM80u2Tc2QoM-1699446336-0-AaTZclpwESvtFgDH7jROJ9L5UpcM50I3GU2jHvlGy9jWhrjniwrt3NgJQxkk3PZs4RQkQLt47f4O9E5h96YxCgc=; path=/; expires=Wed, 08-Nov-23 12:55:36 GMT; domain=.api.openai.com; HttpOnly; Secure; SameSite=None',
    'strict-transport-security': 'max-age=15724800; includeSubDomains',
    'x-ratelimit-limit-requests': '5000',
    'x-ratelimit-limit-tokens': '160000',
    'x-ratelimit-remaining-requests': '4999',
    'x-ratelimit-remaining-tokens': '157399',
    'x-ratelimit-reset-requests': '12ms',
    'x-ratelimit-reset-tokens': '975ms',
    'x-request-id': '7c5bdc547dc2233db7914ef072a18d63'
  },
  error: {
    message: "This model's maximum context length is 4097 tokens. However, your messages resulted in 4945 tokens. Please reduce the length of the messages.",
    type: 'invalid_request_error',
    param: 'messages',
    code: 'context_length_exceeded'
  },
  code: 'context_length_exceeded',
  param: 'messages',
  type: 'invalid_request_error'
}

