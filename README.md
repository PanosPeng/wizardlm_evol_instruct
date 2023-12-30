- 参考项目：https://github.com/nlpxucan/WizardLM/blob/main/Evol_Instruct

```bash
conda create --name wizardlm python=3.9
conda activate wizardlm

pip -q install openai==0.26.0

export OPENAI_API_KEY=sk-Hk3Y5hxD0iFG6EoB9c1158948175485fB6A74c30B1F63dBb
export OPENAI_API_BASE=https://api.aiguoguo199.com/v1

# 该函数使用evol-instruct从alpaca_data_cleaned.json中生成新的任务集,52k的指令量迭代生成4轮（原文筛选完成后保留250k）
# 接受三个参数--output_dir --seed_tasks_path --num_instructions_to_generate
python evol_instruct.py --num_instructions_to_generate 5 
```

# **源代码的问题：**
    1. 使用Chatcompletion()，OPENAI新版本不支持
    2. 原论文最后的筛选部分没公开，现有代码就是直接使用prompt响应生成的指令，没有筛选

# 生成示例
seed: Write a short story in third person narration about a protagonist who has to make an important career decision.
instruction: Describe, in third-person perspective, the tale of a main character facing a critical professional choice, and explore the factors and thought processes involved in their decision-making process. output: 

Jonathan sat at his desk, staring at the two job offers in front of him. After months of searching, he had finally landed his dream job in the tech industry. But now, just as he thought he had everything figured out, he was faced with a critical professional choice.

On one hand, he had been offered a high-paying job at a prestigious company that would provide him with stability and security. On the other hand, he had also received an offer from a startup company that promised him the opportunity to work on cutting-edge technology and be a part of a dynamic, fast-paced team.

Jonathan's mind was in turmoil as he weighed the pros and cons of each option. The first job seemed like a safe and practical choice, but he couldn't help but feel drawn to the excitement and potential of the startup. He had always been an ambitious and adventurous person, and the thought of being a part of something new and innovative was tempting.

But he also had to consider the risks involved in joining a startup. What if it failed? What if he couldn't handle the pressure? These thoughts crept into his mind, causing doubts and uncertainties to cloud his judgement.

Jonathan turned to his family and friends for advice, seeking their opinions and perspectives. Some urged him to take the safe option, reminding him of his financial responsibilities and the importance of stability. Others encouraged him to take a chance and follow his passions, assuring him that he had the skills and determination to succeed.

As he listened to everyone's opinions, Jonathan realized that the decision ultimately rested on his shoulders. He had to listen to his own instincts and make the choice that felt right for him.

After much contemplation, Jonathan made his decision. He chose the startup, driven by his desire for challenge and growth. The risks and uncertainties were there, but he was willing to take them on for the chance to make a difference and be a part of something special.

As he accepted the offer and began his new journey, Jonathan couldn't help but feel a mix of excitement and nervousness. The road ahead may not be easy, but he was ready to face the challenges and embrace the opportunities that lay ahead. In the end, he knew that he had made the right decision for himself and his career. 
evol success!
seed: Evaluate this sentence for spelling and grammar mistakes
instruction: Check this sentence for errors in spelling and grammar to avoid compromising the quality of language and composition.
While completing his meal, he departed from the restaurant with haste. output: 

While finishing his meal, he quickly left the restaurant.
evol success!