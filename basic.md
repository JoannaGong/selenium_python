# 使用 chrome 打开浏览器

```
from selenium import webdriver
browser = webdriver.Chrome()      // 打开浏览器
help(browser.get)                 // 查看浏览器方法
browser.get('http://www.baidu.com')     // 打开一个网页
browser.title                     // 查看浏览器标题
'百度' in browser.title            // 确认浏览器标题中的字，返回Boolean
browser.current_url                // 返回浏览器地址
browser.maximize_window()          // 浏览器最大化
browser.quit()                    // 关闭浏览器
```

# 定位元素

| 元素名称 | webdriver API |
| :---:    | :--- |
| id | find_element_by_id() |
| name | find_element_by_name() |
| class name | find_element_by_class_name() |
| tag name | find_element_by_tag_name() |
| link text | find_element_by_link_text() |
| partial link text | find_element_by_partial_link_text() 模糊查找|
| xpath | find_element_by_xpath() |
| css selector | find_element_by_css_selector() |


# 元素操作方式

| 方法 | 说明 |
| :---:    | :--- |
| clear | 清楚元素内容 |
| send_keys | 模拟按键输入 |
| click | 点击 |
| submit | 提交表单 |

```
ele = browser.find_element_by_id('kw')   // 查找元素
id(ele)    // 元素id
type(ele)
ele.clear()     // 清除输入内容
ele.send_keys('python')      // 输入内容
browser.back()        // 退回到上一页
```


# XPath

* XML 路径语言，用来确定 XML 文档中某部分位置的语言
* XPath 用于在 XML 文档中通过元素和属性进行导航
* XPath 是一个 W3C 标准


## XPath 节点类型

元素、属性、文本、命名空间、指令处理、注释及文档

## XPath 通过路径表达式从 xml 文档中选取节点或节点设置

| 表达式 | 结果 |
| :---:    | :--- |
| /xxx | 选取根节点xxx |
| /xxx/yyy | 选取绝对路径选择元素 |
| //xxx | 整个文档扫描，找到所有xxx元素 |
| //xxx/yyy | 所有父元素为xxx的yyy元素 |
| . | 选取当前节点的父元素节点 |
| .. | 选取父元素地址 |
| //xxx[@id] | 选取所有xxx元素中有id属性的元素 |
| //xxx[@id=yyy] | 选取所有xxx元素id属性为yyy的元素 |

```
b.get(r'G:\python\demo\index.html')

// 绝对路径
ele = b.find_element_by_xpath('/html/body/form/input')
ele.get_attribute('type')
ele1 = b.find_element_by_xpath('/html/body/form/input[2]')

e = b.find_element_by_xpath('//form/input')
e1 = b.find_element_by_xpath('//form/input[2]')
```

# ActionChains 类与输入事件

* from selenium.webdriver.common.action_chains import ActionChains
* ActionChains(driver) 用于生成模拟用户行为
* perform() 执行存储行为


## 鼠标事件

| 表达式 | 说明 |
| :---:    | :--- |
| context_click | 右击事件 |
| double_click | 双击事件 |
| drag_and——drop | 拖动 |
| move_to_element() | 鼠标停在一个元素上 |
| click_and_hold | 按下鼠标左键在一个元素上 |

```
from selenium.webdriver.common.action_chains import ActionChains
ele = b.find_element_by_link_text('软件测试')
ActionChains(b).move_to_element(ele).perform()
```

## 键盘事件 send_keys()
from selenium.webdriver.common.keys import Keys

| 表达式 | 说明 |
| :---:    | :--- |
| send_keys(Keys.BACK_SPACE) | 退格键 |
| send_keys(Keys.CONTRL, 'a') | 全选 |
| send_keys(Keys.CONTRL, 'v') | 粘贴 |
| send_keys(Keys.CONTRL, 'c')() | 复制 |
| send_keys(Keys.CONTRL, 'x') | 剪切 |
| send_keys(Keys.ENTER) | 回车 |

```
ele = b.find_element_by_id('js_keyword')
from selenium.webdriver.common.keys import Keys
ele.send_keys('python')
ele.send_keys(Keys.BACKSPACE)
```


# 对话框处理与登陆测试



