本项目实现了遗传算法。转载自(https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650728869&idx=4&sn=377e2da3d6fe3ec06154d4cc01a9c6e0&scene=0#wechat_redirect)
#### 遗传算法的步骤：
* 初始化
该过程从种群的一组个体开始，且每一个体都是待解决问题的一个候选解。  
个体以一组参数（变量）为特征，这些特征被称为基因，串联这些基因就可以组成染色体（问题的解）。  
在遗传算法中，单个个体的基因组以字符串的方式呈现，通常我们可以使用二进制（1 和 0 的字符串）编码，即一个二进制串代表一条染色体串。因此可以说我们将基因串或候选解的特征编码在染色体中。
* 个体评价（计算适应度函数）
个体评价利用适应度函数评估了该个体对环境的适应度（与其它个体竞争的能力）。每一个体都有适应度评分，个体被选中进行繁殖的可能性取决于其适应度评分。适应度函数值越大，解的质量就越高。适应度函数是遗传算法进化的驱动力，也是进行自然选择的唯一标准，它的设计应结合求解问题本身的要求而定。
* 选择运算
选择运算的目的是选出适应性最好的个体，并使它们将基因传到下一代中。基于其适应度评分，我们选择多对较优个体（父母）。适应度高的个体更易被选中繁殖，即将较优父母的基因传递到下一代。
* 交叉运算
交叉运算是遗传算法中最重要的阶段。对每一对配对的父母，基因都存在随机选中的交叉点。
* 变异运算
在某些形成的新后代中，它们的某些基因可能受到低概率变异因子的作用。这意味着二进制位串中的某些位可能会翻转。  
变异运算可用于保持种群内的多样性，并防止过早收敛。
* 终止
在群体收敛的情况下（群体内不产生与前一代差异较大的后代）该算法终止。也就是说遗传算法提供了一组问题的解。

#### 案例实现
种群的规模恒定。新一代形成时，适应度最差的个体凋亡，为后代留出空间。这些阶段的序列被不断重复，以产生优于先前的新一代。  
这一迭代过程的伪代码:  

START  
Generate the initial population  
Compute fitness  
REPEAT  
    Selection  
    Crossover  
    Mutation  
    Compute fitness  
UNTIL population has converged  
STOP

#### Java 中的实例实现
本项目展示的是遗传算法在 Java 中的示例实现，我们可以随意调试和修改这些代码。给定一组五个基因，每一个基因可以保存一个二进制值 0 或 1。这里的适应度是基因组中 1 的数量。如果基因组内共有五个 1，则该个体适应度达到最大值。如果基因组内没有 1，那么个体的适应度达到最小值。该遗传算法希望最大化适应度，并提供适应度达到最大的个体所组成的群体。注意：本例中，在交叉运算与突变运算之后，适应度最低的个体被新的，适应度最高的后代所替代。