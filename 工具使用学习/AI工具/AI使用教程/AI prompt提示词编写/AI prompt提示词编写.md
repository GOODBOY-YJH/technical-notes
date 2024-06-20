## AI提示词调教模版

[英文调教指南](https://github.com/f/awesome-chatgpt-prompts)

[中文调教指南](https://github.com/PlexPt/awesome-chatgpt-prompts-zh)

## AI提示词原理（省流：讲清楚，做示范）

#### 基础

+ 指令词

  > 例如 
  >
  > 简述XX；解释XX；翻译XX；总结XX；生成XX代码
  >
  > 提示：要清晰和简洁

+ 背景

  > 例如
  >
  > 我是一个XX；你是一个XX；
  >
  > 提示：做角色扮演

+ 输入

  > 例如
  >
  > 总结时提供的文本内容；编写```SQL```代码时提供的数据库/表结构信息...
  >
  > 提示： 使用### XX ### 或者 """ XX """ 将提供的内容分割开

+ 输出

  > 例如
  >
  > 50字；4句话；以```JSON```格式输出
  >
  > 提示：要清晰和简洁



#### 少样本 & 思维链

+ One-Shot 少样本

  > 过程：给一个正确的例子

+ Few-Shot 多样本

  > 过程：给一些正确的例子

+ CoT 思维链

  > 过程：给正确的例子，并且把思维的过程输入给AI（问题解决过程中的每个步骤）
  >
  > 例如：让模型判断用户给出的解决方案是否正确时，先让模型自己给出解决方案，并与用户给出的解决方案进行对比，以获得更好的回复结果。就可以使用下面的步骤。
  >
  > 第一步：自己解决问题。
  >
  > 第二步：用自己的答案和用户的作对比，判断用户的方案是否正确。
  >
  > 第三部：输出用户的解决方案是否正确。
  >
  > 提示：要给出足够多的例子，AI回答才会和我们给出的例子一模一样

+ Zero-Shot + CoT 零样本+思维链

  > 过程：输入prompt。Let's think step by step
  >
  > 提示：AI会自动去推理回答问题

#### 联网 & 认知搜索

+ Search API + GPT

  > 过程：调用网络搜索API，把API的返回结果喂给GPT，并让GPT根据结果生成问题答案。

+ Embedding(嵌入) Search + GPT

  > 过程：Embedding会将输入计算出一个1536位的向量模型。
  >
  > 首先把大段内部资料，切分成GPT能够接受的长度，通过embedding模型转化成向量，保存在本地向量数据库。
  >
  > 然后把用户的问题也转化成向量，然后从数据库中通过计算距离，找到和用户问题最相关的几个片段，最后将这些片段和用户输入的问题，整理成一个prompt，输入到GPT中让GPT总结回答。



#### React实现

+ 简述：让模型进行推理，并自己决定要调用哪个外部工具，再把工具生成的结果告诉模型，模型根据结果再进行推理下一步，直到任务完成。

+ 模版

  ```
  英文：
  
  ===
  
  Answer the following questions as best you can. 		  
  
  
  You have access to the following tools: 				
  
  [{tool_name_and_description}]
  
  
  Use the following format:            			  
  
  
  Question: the input question you must answer			  
  
  Thought: you should always think about what to do		  
  
  Action: the action to take, should be one of [{tool_names}]	 	
  
  Action Input: the input to the action
  
  Observation: the result of the action
  
  
  ... (this Thought/Action/Action Input/Observation can repeat N times) 	
  
  
  Thought: I now know the final answer				 
  
  Final Answer: the final answer to the original input question"""	 	
  
  
  Begin!
  
  
  Question: {input}
  
  Thought:{agent_scratchpad}
  
  
  
  
  中文：
  
  ===
  
  尽可能的去回答以下问题，你可以使用以下的工具：
  
  [{工具名和描述}]
  
  
  请使用以下格式回答：
  
  
  问题: 你必须回答的问题
  
  
  思考: 你应该一直保持思考，思考要怎么解决问题
  
  动作: <工具名>。每次动作只选择一个工具。工具列表 [{工具名和描述}]
  
  输入: <调用工具时需要传入的参数>
  
  观察: <第三方工具返回的结果>
  
  
  ... 这个“思考-动作-输入-观察”的循环可以重复N次
  
  
  思考: 最后，你应该知道最终结果了
  
  最终结果: 针对于原始问题，输出最终结果
  
  
  开始！
  
  
  问题: {问题}
  
  思考:
  ```

  