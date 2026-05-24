## 1. 格式

### 1. 缩进统一使用 4 个空格

```cpp
// 正确：4 个空格缩进
void foo()
{
    if (condition) {
        doSomething();       // 4 个空格
        doMore();            // 4 个空格
    }
}

// 错误：Tab 或 2 个空格
void foo()
{
  if (condition) {           // 2 个空格，错误
	  doSomething();         // Tab，错误
  }
}
```

### 2. namespace、struct、class、enum、union、函数定义使用 Allman 风格

```cpp
// 正确：左花括号独占一行（Allman 风格）
namespace my_namespace
{

class MyClass
{
};

struct MyStruct
{
};

enum class MyEnum
{
};

union MyUnion
{
};

void myFunction()
{
}

// 错误：左花括号在行尾
namespace my_namespace {
class MyClass {
void myFunction() {
```

### 3. if、else、for、while、switch 使用 K&R 风格

```cpp
// 正确：左花括号在行尾（K&R 风格）
if (x > 0) {
    doPositive();
} else if (x < 0) {
    doNegative();
} else {
    doZero();
}

for (int i = 0; i < n; ++i) {
    process(i);
}

while (running) {
    tick();
}

switch (value) {
case 1:
    handleOne();
    break;
default:
    handleDefault();
    break;
}

// 错误：控制语句使用 Allman
if (x > 0)
{
    doPositive();
}
```

### 4. 控制语句即使只有一行，也必须使用花括号

```cpp
// 正确：即使只有一行也加花括号
if (ready) {
    launch();
}

for (auto& item : items) {
    item.reset();
}

// 错误：单行语句省略花括号
if (ready)
    launch();          // 禁止

for (auto& item : items)
    item.reset();      // 禁止
```

### 5. ,、; 后必须加一个空格

```cpp
// 正确：逗号和分号后加空格
void func(int a, int b, int c);
int x, y, z;

for (int i = 0; i < n; ++i) {   // 分号后有空格
    process(i);
}

// 错误：逗号和分号后无空格
void func(int a,int b,int c);    // 逗号后无空格
for (int i = 0;i < n;++i) {     // 分号后无空格
```

### 6. 运算符和比较符两侧必须加空格

```cpp
// 正确：运算符和比较符两侧加空格
int sum = a + b;
bool ok = (x >= 0) && (y < max);
int result = value * factor + offset;
auto it = vec.begin();

// 错误：两侧无空格
int sum=a+b;
bool ok=(x>=0)&&(y<max);
```

### 7. 圆括号和花括号之间必须加一个空格

```cpp
// 正确：括号和花括号之间加空格
if (condition) {
    doWork();
}

while (running) {
    tick();
}

try {
    riskyOp();
} catch (const std::exception& e) {
    handle(e);
}

// 错误：括号和花括号之间无空格
if (condition){
    doWork();
}
while (running){
    tick();
}
```

---

## 2. 命名

### 1. 命名必须清晰、完整、具有描述性

```cpp
// 正确：清晰完整的名称
int maxRetryCount;
std::string userDisplayName;
void calculateMonthlyAverage();

// 错误：含义不清
int n;                         // 不知道 n 表示什么
std::string s;                 // 不知道 s 表示什么
void calc();                   // 缩写且不清晰
```

### 2. 禁止使用含义不清的缩写

```cpp
// 正确：不缩写或使用公认缩写
int connectionCount;
int configurationIndex;
std::string previousAddress;

// 错误：任意缩写
int connCnt;                   // 应为 connectionCount
int cfgIdx;                    // 应为 configurationIndex
std::string prevAddr;          // 应为 previousAddress
```

### 3. 文件名必须全部小写，可使用下划线

```cpp
// 正确：全小写 + 下划线
// 文件命名示例：
//   my_class.h
//   my_class.cpp
//   data_processor.h
//   data_processor.cpp
//   network_util.h
//   network_util.cpp

// 错误：大写或驼峰
//   MyClass.h
//   DataProcessor.cpp
//   NetworkUtil.h
```

### 4. 类型名使用大写驼峰命名法

```cpp
// 正确：大写驼峰（UpperCamelCase / PascalCase）
class FileManager {};
class HttpConnection {};
struct Point3D {};
enum class ColorMode {};
using StringList = std::vector<std::string>;

// 错误：小写或下划线
class file_manager {};         // 下划线，错误
class httpConnection {};       // 小写开头，错误
```

### 5. 变量名使用小写字母 + 下划线

```cpp
// 正确：全小写 + 下划线（snake_case）
int file_count;
std::string user_name;
double average_score;
bool is_connected;
const int kMaxRetryCount = 3;

// 错误：驼峰命名
int fileCount;                 // 驼峰，错误
std::string userName;          // 驼峰，错误
```

### 6. 类成员变量必须以下划线结尾

```cpp
// 正确：成员变量以 _ 结尾
class MyClass
{
public:
    void setName(const std::string& name) { name_ = name; }

private:
    std::string name_;
    int count_;
    double speed_;
};

// 错误：无下划线结尾
class MyClass
{
private:
    std::string name;          // 缺少 _
    int count;                 // 缺少 _
};
```

### 7. 结构体成员变量不以下划线结尾

```cpp
// 正确：结构体成员无下划线结尾
struct Point
{
    double x;
    double y;
    double z;
};

struct Rect
{
    int width;
    int height;
};

// 不像类成员那样加下划线
// struct Point { double x_; double y_; }; // 错误
```

### 8. 函数名使用小写驼峰命名法

```cpp
// 正确：小写驼峰（lowerCamelCase）
void startEngine();
int getCurrentIndex() const;
bool isDataValid() const;
void processRequest(const Request& req);

// 错误：下划线或大写驼峰
void start_engine();           // 下划线，错误
int GetCurrentIndex();         // 大写驼峰，错误
```

### 9. 命名空间使用小写字母 + 下划线

```cpp
// 正确：全小写 + 下划线
namespace my_project {}
namespace network_utils {}
namespace data_processing {}

// 错误：驼峰或大写
namespace MyProject {}         // 大写驼峰，错误
namespace NetworkUtils {}      // 大写驼峰，错误
```

### 10. 宏使用全大写字母 + 下划线

```cpp
// 正确：全大写 + 下划线
#define MAX_BUFFER_SIZE 4096
#define LOG_ERROR(msg) fprintf(stderr, "[ERROR] %s\n", msg)
#define ARRAY_LENGTH(arr) (sizeof(arr) / sizeof((arr)[0]))

// 错误：小写或驼峰
#define MaxBufferSize 4096     // 驼峰，错误
#define log_error(msg) ...     // 小写，错误（容易与函数混淆）
```

### 11. 枚举优先使用 enum class，枚举值使用大写驼峰命名法

```cpp
// 正确：使用 enum class，枚举值大写驼峰
enum class ConnectionState
{
    Disconnected,
    Connecting,
    Connected,
    Disconnecting,
};

enum class LogLevel
{
    Debug,
    Info,
    Warning,
    Error,
};

ConnectionState state = ConnectionState::Connected;

// 错误：不使用 enum class，或枚举值命名不规范
enum ConnectionState
{
    DISCONNECTED,              // 旧式 enum，且命名风格错误
    CONNECTED,
};
```

### 12. 旧式 enum 的枚举值必须带类型前缀

```cpp
// 正确：旧式 enum（C 兼容场景）带类型前缀
enum Color
{
    ColorRed,
    ColorGreen,
    ColorBlue,
};

enum AnimalType
{
    AnimalTypeDog,
    AnimalTypeCat,
    AnimalTypeBird,
};

// 错误：旧式 enum 无前缀（容易命名冲突）
enum Color
{
    Red,                       // 可能与其他 enum 冲突
    Green,
    Blue,
};
```

### 13. C 风格接口必须使用模块名或类型名前缀

```cpp
// 正确：C 风格接口使用前缀（配合 C 链接）
extern "C" {

// 模块前缀
int file_utils_open(const char* path);
int file_utils_close(int handle);
int file_utils_read(int handle, char* buf, int size);

// 类型名前缀
struct List;
List* list_create();
void list_destroy(List* list);
int list_size(const List* list);

} // extern "C"

// 错误：无前缀的 C 接口（容易全局命名冲突）
extern "C" {
int open(const char* path);    // 冲突风险高
int read(int h, char* b, int s);
}
```

### 14. 与标准库、Qt 或第三方框架深度集成时，可遵循其既有风格

```cpp
// 正确：Qt 集成时遵循 Qt 风格（驼峰命名、信号槽等）
class MyWidget : public QWidget
{
    Q_OBJECT

public:
    explicit MyWidget(QWidget* parent = nullptr);

signals:
    void dataReady(const QByteArray& data);   // Qt 风格命名

private slots:
    void onButtonClicked();                    // Qt 风格命名
};

// 正确：STL 风格代码遵循标准库命名
// 例如，自定义迭代器使用与 STL 一致的 typedef：
template<typename T>
class MyContainer
{
public:
    using value_type = T;          // 遵循 STL 命名惯例
    using iterator = T*;           // 遵循 STL 命名惯例
    using const_iterator = const T*;
};
```

---

## 3. 代码文件

### 1. .cpp 文件中，对应头文件必须放在 #include 第一位

```cpp
// ======== my_class.cpp ========

// 正确：自己的头文件放在最前面
#include "my_class.h"

#include <cstdio>
#include <vector>

#include "other_module.h"
```

### 2. 其余头文件按稳定性从高到低排列：C 标准库、C++ 标准库、第三方库、公司内部库、工程内部头文件

```cpp
// ======== my_class.cpp ========

// 第 1 组：对应头文件
#include "my_class.h"

// 第 2 组：C 标准库
#include <cstdio>
#include <cstdlib>
#include <cstring>

// 第 3 组：C++ 标准库
#include <algorithm>
#include <memory>
#include <string>
#include <vector>

// 第 4 组：第三方库
#include <boost/asio.hpp>
#include <fmt/core.h>

// 第 5 组：公司内部库
#include <company/network/socket.h>
#include <company/utils/logger.h>

// 第 6 组：工程内部头文件
#include "project/data_processor.h"
#include "project/network_manager.h"
```

### 3. 头文件中必须优先使用前置声明，避免不必要的 #include

```cpp
// ======== my_class.h ========

// 正确：使用前置声明代替 #include
class DataProcessor;       // 前置声明
class NetworkManager;      // 前置声明
struct Config;

class MyClass
{
public:
    void setProcessor(DataProcessor* processor);   // 指针/引用可用前置声明
    void setConfig(const Config& config);

private:
    DataProcessor* processor_;  // 前置声明即可
    Config config_;             // 如果这里用的是值类型，
                                // 则 .cpp 中才需要 #include "config.h"
};

// 错误：不必要时也 #include
// #include "data_processor.h"   // 仅用指针/引用时不必要
// #include "network_manager.h"
// #include "config.h"
```

### 4. 对外接口头文件和外部库头文件必须从工程 include 根目录开始引用

```cpp
// 正确：从 include 根目录开始引用
#include <my_project/api/client.h>        // 对外接口
#include <my_project/common/types.h>      // 对外接口

// 假定 include 根路径是 project_root/include
// 目录结构：project_root/include/my_project/api/client.h
//           project_root/include/my_project/common/types.h

// 错误：使用相对路径
// #include "../api/client.h"         // 禁止相对路径
// #include "client.h"                // 禁止（对外接口应从根目录引用）
```

### 5. 内部头文件路径可根据工程结构配置

```cpp
// 正确：内部头文件按工程配置的路径引用
// 假定 CMake 或构建系统配置了内部 include 路径

#include "core/engine.h"             // 工程内部，按配置路径
#include "utils/string_helper.h"     // 工程内部
#include "detail/impl_private.h"     // 工程内部

// 也可以使用相对路径（仅限内部、同模块头文件）
#include "engine.h"                  // 同目录下可直接引用
```

---

## 4. 作用域

### 1. 禁止使用全局变量

```cpp
// 错误：全局变量
// int g_counter = 0;                // 禁止
// std::string g_config_path;        // 禁止

// 正确：使用封装替代全局变量
class AppContext
{
public:
    static AppContext& instance()
    {
        static AppContext ctx;
        return ctx;
    }

    int counter() const { return counter_; }
    void setCounter(int c) { counter_ = c; }

private:
    AppContext() = default;
    int counter_ = 0;
};
```

### 2. 避免定义全局函数，函数必须放入明确的命名空间

```cpp
// 正确：函数放入命名空间
namespace file_utils
{

bool exists(const std::string& path)
{
    struct stat st;
    return stat(path.c_str(), &st) == 0;
}

} // namespace file_utils

// 使用：file_utils::exists("/tmp/test");

// 错误：全局函数
// bool fileExists(const std::string& path);  // 禁止
```

### 3. 仅在单个 .cpp 文件中使用的函数、类型或变量，必须放入匿名命名空间

```cpp
// ======== my_module.cpp ========

// 正确：内部使用的符号放入匿名命名空间
namespace
{

const int kLocalMaxRetry = 5;

struct InternalData
{
    int id;
    std::string key;
};

void helperFunction(InternalData& data)
{
    data.key = "processed";
}

} // anonymous namespace

// 公开接口
void processData()
{
    InternalData d{1, "init"};
    helperFunction(d);
}

// 错误：内部函数暴露为全局（或在 .h 中声明）
// void helperFunction();  // 不应暴露
```

### 4. 头文件中禁止使用 using namespace

```cpp
// ======== my_header.h ========

// 正确：禁止 using namespace
#include <string>
#include <vector>

namespace my_project
{

void process(const std::vector<std::string>& items);  // 使用完整限定名

} // namespace my_project

// 错误：头文件中的 using namespace
// using namespace std;                  // 禁止
// using namespace my_project;           // 禁止
// namespace mp = my_project;            // 命名空间别名也应谨慎
```

---

## 5. 类

### 1. 类成员按 public、protected、private 顺序声明

```cpp
class MyClass
{
public:          // 第一组：public
    // ...

protected:       // 第二组：protected
    // ...

private:         // 第三组：private
    // ...
};
```

### 2. 每个访问级别内按以下顺序声明：嵌套类型、常量、构造函数、析构函数、成员函数、数据成员

```cpp
class DataProcessor
{
public:
    // 嵌套类型
    enum class Mode { Fast, Accurate };
    using Result = std::pair<int, std::string>;

    // 常量
    static const int kDefaultPort = 8080;

    // 构造函数
    DataProcessor();
    explicit DataProcessor(Mode mode);

    // 析构函数
    ~DataProcessor();

    // 成员函数
    void setMode(Mode mode);
    Mode mode() const;
    Result process(const std::string& input);

protected:
    // 嵌套类型
    struct InternalState {};

    // 常量
    static const int kBufferSize = 4096;

    // 构造函数
    DataProcessor(int reserved);

    // 析构函数（通常不需要 protected 析构函数，此处仅为示例）
    // ~DataProcessor();

    // 成员函数
    virtual void onPreProcess();
    virtual void onPostProcess();

    // 数据成员
    InternalState state_;

private:
    // 嵌套类型
    struct Pimpl;

    // 常量
    static const int kMaxQueueSize = 100;

    // 构造函数（如禁用拷贝）
    DataProcessor(const DataProcessor&) = delete;

    // 成员函数
    void internalValidate();

    // 数据成员
    Mode mode_ = Mode::Fast;
    std::unique_ptr<Pimpl> pimpl_;
};
```

### 3. .cpp 文件中的函数实现顺序应与声明顺序一致

```cpp
// ======== data_processor.h ========
class DataProcessor
{
public:
    void stepA();
    void stepB();
    void stepC();

private:
    void helperX();
    void helperY();
};

// ======== data_processor.cpp ========

// 正确：实现顺序与声明顺序一致
void DataProcessor::stepA() { /* ... */ }
void DataProcessor::stepB() { /* ... */ }
void DataProcessor::stepC() { /* ... */ }
void DataProcessor::helperX() { /* ... */ }
void DataProcessor::helperY() { /* ... */ }

// 错误：实现顺序与声明不一致
// void DataProcessor::stepC() { /* ... */ }
// void DataProcessor::stepA() { /* ... */ }
// void DataProcessor::helperY() { /* ... */ }
```

### 4. 优先使用组合，谨慎使用继承

```cpp
// 正确：使用组合（composition）
class Car
{
public:
    void start()
    {
        engine_.ignite();
        wheels_.roll();
    }

private:
    Engine engine_;       // 组合：Car 包含 Engine
    Wheels wheels_;       // 组合：Car 包含 Wheels
    // 不需要继承 Engine 或 Wheels
};

// 只有明确的 "is-a" 关系时才使用继承
class ElectricCar : public Car    // ElectricCar is-a Car
{
public:
    void chargeBattery() { /* ... */ }
};
```

### 5. 继承必须使用 public

```cpp
// 正确：public 继承
class Dog : public Animal
{
};

// 如果需要 "is-implemented-in-terms-of" 关系，使用组合而非 private 继承
class MySet
{
private:
    std::vector<int> data_;       // 组合优于 private 继承
};

// 错误：非 public 继承
// class Dog : private Animal {};   // 不应使用 private 继承
// class Dog : protected Animal {}; // 不应使用 protected 继承
```

### 6. 包含虚函数的基类，其析构函数必须为 virtual

```cpp
// 正确：有虚函数的基类，析构函数为 virtual
class Base
{
public:
    virtual ~Base() = default;                // virtual 析构函数
    virtual void process() = 0;
};

class Derived : public Base
{
public:
    ~Derived() override = default;            // override（可选但推荐）
    void process() override { /* ... */ }
};

// 错误：基类有虚函数但析构函数非 virtual（导致通过基类指针删除子类对象时行为未定义）
// class Base
// {
// public:
//     ~Base() = default;                     // 非 virtual，错误
//     virtual void process() = 0;
// };
```

### 7. 子类覆写虚函数时必须显式使用 override

```cpp
// 正确：使用 override 关键字
class Animal
{
public:
    virtual ~Animal() = default;
    virtual void speak() const = 0;
    virtual void move() {}
};

class Dog : public Animal
{
public:
    void speak() const override;        // 显式 override
    void move() override;               // 显式 override
};

// 错误：不使用 override（可能因签名不符而意外创建新虚函数）
// class Dog : public Animal
// {
// public:
//     void speak() const;              // 缺少 override，编译器不检查
//     void move();                     // 缺少 override，可能不是真正的覆写
// };
```

---

## 6. 函数

### 1. 函数参数必须按输入参数、输出参数的顺序排列

```cpp
// 正确：输入参数在前，输出参数在后
bool readFile(const std::string& path,         // 输入
              std::string& content,            // 输出
              std::string* error_msg = nullptr); // 输出（可选）

void transform(const InputData& input,         // 输入
               OutputData* output);            // 输出（指针表示可选/可为空）

// 错误：输出参数在输入参数前面
// bool readFile(std::string& content,          // 输出在前，错误
//               const std::string& path);      // 输入在后
```

### 2. 禁止使用既作为输入又作为输出的参数

```cpp
// 正确：输入和输出分离
struct Request
{
    std::string path;
};

struct Response
{
    int code;
    std::string body;
};

bool handleRequest(const Request& req, Response* resp);

// 错误：同一个参数既输入又输出（in-out 参数）
// bool handleRequest(Request& data);   // data 同时是输入和输出，不清晰

// 如果确实需要 in-out 语义，应拆分为两个参数或使用返回值
// 正确做法 1：拆分为输入和输出参数
void enrichData(const RawData& input, EnrichedData* output);

// 正确做法 2：返回值携带输出，避免修改输入
EnrichedData enrichData(const RawData& input);
```

---

## 7. 注释

### 1. 注释必须以中文为主，专业名词使用英文并补充中文含义

```cpp
// 正确：中文为主，专业名词保留英文并补充中文
// 使用 RAII（Resource Acquisition Is Initialization，资源获取即初始化）管理文件句柄
class FileGuard {};

// 初始化 TCP（Transmission Control Protocol，传输控制协议）连接池
void initTcpPool();

// 错误：全英文注释
// Initialize the TCP connection pool
```

### 2. 注释优先使用 //，必要时使用 /* \*/

```cpp
// 正确：单行或短注释使用 //
int max_retry = 3;  // 最大重试次数

// 较长的多行注释也优先使用 //
// 这个函数处理以下场景：
// 1. 缓冲区为空时自动填充
// 2. 填充失败时触发错误恢复
// 3. 恢复失败时记录日志并返回错误码

// 必要时刻使用 /* */（例如需要临时注释掉一段代码用于调试时）
/*
 * 多行文档注释也可以使用此风格（如果项目工具链要求）
 * 但日常仍优先使用 //
 */
```

### 3. 每个文件开头必须包含版权公告

```cpp
// ======== my_module.h ========
/*
 * Copyright (c) 2026 <公司名称>. All rights reserved.
 *
 * 该文件是 <项目名称> 的一部分。未经授权，不得复制、分发或使用。
 */

// 文件内容开始...

// ======== my_module.cpp ========
/*
 * Copyright (c) 2026 <公司名称>. All rights reserved.
 */

// 文件内容开始...
```

### 4. 禁止在 .h 和 .cpp 文件之间复制相同注释

```cpp
// ======== my_module.h ========
// 头文件中写完整注释
// 计算两个日期之间的工作日天数
int countWorkingDays(const Date& start, const Date& end);

// ======== my_module.cpp ========

// 正确：.cpp 中不再复制头文件的注释
int countWorkingDays(const Date& start, const Date& end)
{
    // 只注释实现细节
    int count = 0;
    Date current = start;
    while (current != end.next()) {
        if (!isWeekend(current)) {
            ++count;
        }
        current = current.next();
    }
    return count;
}

// 错误：.cpp 中复制了头文件已有的注释
// int countWorkingDays(const Date& start, const Date& end)
// // 计算两个日期之间的工作日天数    <-- 不要在 .cpp 中重复
// {
//     ...
// }
```

### 5. 类定义前应添加类注释，功能显而易见时可省略

```cpp
// 需要注释：功能复杂的类
// TCP（Transmission Control Protocol，传输控制协议）客户端连接
// 负责管理连接生命周期，包括自动重连、心跳检测和超时处理
class TcpClient
{
public:
    // ...
};

// 可省略注释：功能显而易见的简单结构体
struct Point
{
    double x;
    double y;
};
```

### 6. 函数声明前应添加函数注释，简单取值和设值函数可省略

```cpp
class DataBuffer
{
public:
    // 需要注释：复杂逻辑的函数
    // 将数据写入缓冲区，如果空间不足则自动扩容并触发回调通知
    // 返回实际写入的字节数，出错时返回 -1
    int write(const uint8_t* data, size_t size);

    // 可省略注释：简单的 getter/setter
    size_t size() const { return size_; }
    void setCapacity(size_t cap) { capacity_ = cap; }

private:
    size_t size_ = 0;
    size_t capacity_ = 0;
};
```

### 7. 函数定义处只注释实现细节、关键算法和特殊处理

```cpp
int DataBuffer::write(const uint8_t* data, size_t size)
{
    // 检查是否需要扩容
    if (size_ + size > capacity_) {
        // 扩容策略：1.5 倍增长，至少容纳新数据
        size_t new_cap = std::max(capacity_ * 3 / 2, size_ + size);
        buffer_.resize(new_cap);
        capacity_ = new_cap;
    }

    // 使用 memmove 而非 memcpy，因为源和目标可能重叠
    // （在环回模式下 data 可能指向 buffer_ 内部）
    std::memmove(buffer_.data() + size_, data, size);
    size_ += size;
    return static_cast<int>(size);
}
```

### 8. 类数据成员应在必要时说明用途、特殊值、生命周期或依赖关系

```cpp
class ConnectionPool
{
private:
    int max_connections_;            // 最大连接数，0 表示不限制
    int active_connections_ = 0;     // 当前活跃连接数

    // 空闲连接超时时间（毫秒），-1 表示永不超时
    int idle_timeout_ms_ = 30000;

    // 连接数达到上限时的等待队列；
    // 生命周期由 pool_ 持有，不可单独释放
    WaitQueue* wait_queue_ = nullptr;
};
```

### 9. 复杂、晦涩、关键的代码段前必须添加注释

```cpp
void shiftBits(uint32_t* data, size_t len, int n)
{
    if (n <= 0 || len == 0) {
        return;
    }

    // 按位右移 n 位，跨字边界处理：
    // 每个 32 位字的高 n 位来自前一个字的低 n 位
    // 例如：n=4 时，字 1 的低 4 位将成为字 0 的高 4 位
    const int word_bits = 32;
    const uint32_t mask = (1u << n) - 1;

    for (size_t i = len - 1; i > 0; --i) {
        data[i] = (data[i] >> n) | ((data[i - 1] & mask) << (word_bits - n));
    }
    data[0] >>= n;
}
```

### 10. 行尾注释前保留两个空格

```cpp
// 正确：行尾注释前两个空格
int max_count = 100;  // 最大计数上限
process(data);        // 处理数据，内部会做去重

// 错误：行尾注释前只有一个空格
// int max_count = 100; // 最大计数上限    <-- 只有一个空格
// process(data); // 处理数据
```

### 11. 避免在调用点依赖注释解释参数含义

```cpp
// 正确：使用具名变量或枚举使参数含义自明
const bool enable_cache = true;
const bool enable_logging = false;
initService(enable_cache, enable_logging);

// 更优：使用配置结构体
struct ServiceConfig
{
    bool enable_cache = true;
    bool enable_logging = false;
    int max_connections = 10;
};
initService(config);

// 错误：裸字面量 + 注释解释（注释容易过时）
// initService(true,   // 启用缓存    <-- 不推荐
//             false,  // 不启用日志
//             10);    // 最大连接数
```

### 12. TODO 注释必须包含 git 邮箱

```cpp
// 正确：TODO 包含邮箱
// TODO(zhangsan@company.com): 后续支持 IPv6 地址解析
// TODO(lisi@company.com): 当前实现 O(n²)，需优化为 O(n log n)

// 错误：无邮箱的 TODO
// TODO: 优化性能                       // 不知道谁来负责
// TODO: 加个错误处理                   // 无法追踪责任人
```

### 13. 弃用接口必须使用 DEPRECATED 标记，并包含标识信息

```cpp
// 正确：使用 DEPRECATED 宏标记
#define DEPRECATED(msg, author, date) \
    [[deprecated("[" #author "][" #date "] " msg)]]

// 标记弃用接口
DEPRECATED("使用 processV2() 替代，该接口性能更好", zhangsan, 2026-01-15)
void processV1(const Data& data);

DEPRECATED("该类型设计有缺陷，请使用 NewConfig", lisi, 2025-12-01)
struct OldConfig
{
    int port;
};

// 使用时编译器会给出警告：
// warning: 'processV1' is deprecated:
// [zhangsan][2026-01-15] 使用 processV2() 替代，该接口性能更好
```

---

## 8. 其他

### 1. 尽可能使用 const

```cpp
// 正确：尽可能使用 const 声明常量或不可变数据
const int max_size = 1024;                      // 常量
const std::string app_name = "MyApp";           // 不可变字符串

std::vector<int> numbers = {1, 2, 3, 4, 5};
for (const auto& n : numbers) {                 // 循环中不修改时用 const
    std::cout << n;
}

auto it = numbers.cbegin();                     // 优先用 cbegin/cend 获取 const 迭代器
```

### 2. 只读变量、只读引用参数、返回只读引用、不修改对象状态的成员函数必须使用 const

```cpp
class Config
{
public:
    // 不修改对象状态的成员函数 → const
    int port() const { return port_; }
    std::string host() const { return host_; }

    // 只读引用参数 → const&
    void merge(const Config& other)              // other 只读
    {
        port_ = other.port_;
        host_ = other.host_;
    }

    // 返回只读引用 → const&
    const std::string& rawData() const { return raw_data_; }

private:
    int port_ = 0;
    std::string host_;
    std::string raw_data_;

    // 只读局部变量 → const
    void validate() const
    {
        const int min_port = 1024;               // 只读局部变量
        if (port_ < min_port) {
            // ...
        }
    }
};

// 只读引用参数
void printConfig(const Config& cfg)
{
    std::cout << cfg.host() << ":" << cfg.port();
}
```

### 3. 指针相关 const 写法统一使用 const int *name

```cpp
// 正确：统一使用 "const T *" 形式（const 在类型前面）
void readOnlyPtr(const int* value);              // const 在 int 前面
void readOnlyString(const char* str, size_t len); // const 在 char 前面

const int* findValue(const std::vector<int>& data);
int* const p = &some_int;                       // 指针本身为 const（特殊情况）

// 错误：不用 "int const *" 形式
// void readOnlyPtr(int const *value);           // 不使用此形式
// int const *findValue(const std::vector<int>& data);
```

### 4. 禁止注释掉废弃代码，废弃代码必须直接删除

```cpp
// 正确：废弃代码直接删除（可通过 git 历史找回）

// 如果旧接口仍被外部使用，使用 DEPRECATED 标记引导迁移（见 7.13）

// 错误：注释掉的废弃代码
// void oldFunction()
// {
//     // 旧实现...    <-- 不要这样做，应直接删除
// }
//
// int old_counter = 0;  // 旧变量，已废弃   <-- 应删除
```
