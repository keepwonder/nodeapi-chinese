# 目录
+ [Assert](./assert.md#1)
 - [assert.fail(actual,expected,message,operator)](./assert.md#2)
 - [assert(value[,message]),assert.ok(value[,message])](./assert.md#3)
 - [assert.equal(actual,expected[,message])](./assert.md#4)
 - [assert.notEqual(actual,expected(,message))](./assert.md#5)
 - [assert.deepEqual(actual,expected[,message])](./assert.md#6)
 - [assert.notDeepEqual(actual,expected[,message])](./assert.md#7)
 - [assert.strictEqual(actual,expected[,message])](./assert.md#8)
 - [assert.notStrictEqual(actual,expected[,message])](./assert.md#9)
 - [assert.throws(block[,errot][,message])](./assert.md#10)
 - [assert.doesNotThrow(block[,message])](./assert.md#11)
 - [assert.ifError(value)](./assert.md#12)

# <a name="1"> Assert
    稳定性：5 - 锁定状态
该模块用于单元测试，可以通过require('assert')引入
## <a name="2"> asser.fail(actual,expected,message,operator)
抛出一个异常，用提供的operator来分开真实值和期望值
## <a name="3"> assert(value[,message]),assert.ok(value[,message])
测试值是否为真，和assert.equal(true, !!value, message)等效
## <a name="4"> assert.equal(actual,expected[,message])
测试是否相等，和==比较操作符一样
## <a name="5"> assert.notEqual(actual,expected[,message])
测试是否不等，和!=比较操作符一样
## <a name="6"> assert.deepEqual(actual,expected[,message])
测试是否全等
## <a name="7"> assert.notDeepEqual(actual,expected[,message])
测试是否不全等
## <a name="8"> assert.strictEqual(actual,expected[,message])
测试是否严格相等，和===比较操作符一样
## <a name="9"> assert.notStrictEqual(actual,expected[,message])
测试不严格相等，和!==比较操作符一样
## <a name="10"> assert.throws(block[,error][,message])
期待block抛出一个错误，错误可以是构造器，正则表达式或者验证函数

使用构造器验证：

    assert.throws(
        function() {
            throw new Error("Wrong value");
            },
            Error
        );

使用正则验证错误信息：

    assert.throws(
        function() {
            throw new Error("Wrong value");
            },
            /value/
        );

客户端错误验证

    assert.throws(
        function() {
            throw new Error("Wrong value");
            },
            function(err) {
                if( (err instanceof Error) && /value/.test(err) ){
                    return true;
                }
            },
            "unexpected error";
        );

## <a name="11"> asset.doesNotThrow(block[,message])
期望代码块不抛出错误，详见assert.throws
## <a name="12"> assert.ifError(value)
测试值是否不是一个假值，如果是真值则抛出错误，在测试回调函数第一个参数error时非常有用