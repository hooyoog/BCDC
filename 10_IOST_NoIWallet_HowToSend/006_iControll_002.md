# POST传参获得json返回值-打印


智能合约   
```javascript
iControll(iTools, tableName, tableField, Value) {
    this._is_Admin();
    if (iTools === "iSetOne") {
        storage.mapPut(tableName, tableField, Value);
        return "iSetOne | " + tableName + "|" + tableField + "|" + Value + "|"
    } else if (iTools === "iGetOne") {
        return storage.mapGet(tableName, tableField)
    } else if (iTools === "iGetLen") {
        return storage.mapLen(tableName)
    } else if (iTools === "iGetAll") {
        return storage.mapKeys(tableName)
    } else if (iTools === "iGetHas") {
        return storage.mapHas(tableName, tableField)
    } else if (iTools === "iDelOne") {
        storage.mapDel(tableName, tableField)
        return "iDelOne | " + tableName + "|" + tableField + "|"
    } else {
        throw "iTools wrong !"
    }
}
```