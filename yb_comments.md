
# 2020-10-30

Согласно инструкции https://youtu.be/CpuiFW7fwZ0 переводил приложение на heroku c mdLab на Atlas (Mongo) 

После запуска получил 

```
Oops - Nightscout is having trouble
Don't panic, we can work this out! This happens to the best of us.

Check the errors below and then refer to the troubleshooting documentation.

Errors occurred during startup:
Unable to setup authorization
{"stack":"MongoError: user is not allowed to do action [find] on [.auth_roles]
at Connection. (/app/node_modules/mongodb/lib/core/connection/pool.js:451:61)
at Connection.emit (events.js:198:13)
at processMessage (/app/node_modules/mongodb/lib/core/connection/connection.js:452:10)
at TLSSocket. (/app/node_modules/mongodb/lib/core/connection/connection.js:621:15)
at TLSSocket.emit (events.js:198:13)
at addChunk (_stream_readable.js:288:12)
at readableAddChunk (_stream_readable.js:269:11)
at TLSSocket.Readable.push (_stream_readable.js:224:10)
at TLSWrap.onStreamRead [as onread] (internal/stream_base_commons.js:94:17)","message":"user is not allowed to do action [find] on [.auth_roles]","ok":0,"code":8000,"codeName":"AtlasError","name":"MongoError"}
```

Пришлось
1. Обновить приложение, сначала обновив fork репозитория (https://gist.github.com/CristinaSolana/1885435), а потом обновив из fork'а само приложение на heroku (https://f-a.nz/dev/update-deploy-to-heroku-app/)
2. Использовать для `MONGODB_URI` значение для драйвера Node.js версии 3.6 и выше:
mongodb+srv://heroku_s8h470q5:<password>@cluster-s8h470q5.su1dn.mongodb.net/<dbname>?retryWrites=true&w=majority
указав там не только `<password>`, но и `<dbname>`


