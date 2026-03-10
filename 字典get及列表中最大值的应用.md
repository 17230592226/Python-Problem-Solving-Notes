#  题目：（字典实战：数据统计）
已知列表score_list = [ {"name":"张三","subject":"数学","score":90}, {"name":"张三","subject":"语文","score":85}, {"name":"李四","subject":"数学","score":88}, {"name":"李四","subject":"语文","score":92}, {"name":"王五","subject":"数学","score":95} ]  
要求：  
> 统计每个学生的总分，生成新字典total_score，格式为{"张三": 总分, "李四": 总分, ...}；  
找出总分最高的学生姓名和分数。  
核心考察点：
- 字典的遍历、新增 / 修改键值对；  
- 列表 + 字典的嵌套遍历；  
- 字典的最值查找。  

# 代码
```
score_list = [
    {"name":"张三","subject":"数学","score":90},
    {"name":"张三","subject":"语文","score":85},
    {"name":"李四","subject":"数学","score":88},
    {"name":"李四","subject":"语文","score":92},
    {"name":"王五","subject":"数学","score":95}
]

# 第一步：统计总分（基础写法）
total_score = {}
for item in score_list:
    name = item["name"]
    total_score[name] = total_score.get(name, 0) + item["score"]  # 简化的if判断写法

# 第二步：用max()函数简洁找最高分（核心优化）
# key=lambda x: x[1] 表示按元组的第二个元素（分数）比较
max_item = max(total_score.items(), key=lambda x: x[1])
print(type(max_item))
print(max_item)
max_name = max_item[0]  # 最高分学生姓名
max_score = max_item[1] # 最高分

print("总分字典：", total_score)
print(f"总分最高的学生：{max_name}，分数：{max_score}")
```
