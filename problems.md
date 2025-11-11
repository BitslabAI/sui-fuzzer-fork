problems:
1. fuzz_init只有一个函数，无法进行多阶段的初始化，比如先生成一个Registry，再通过registry生成Pool
2. 只支持一个module的fuzz，也就是至少需要给每个module编写一个fuzz_init，会破坏原有代码的完整性并且要付出的efforts过多
3. 不支持address, u256 输入, 不支持Coin Balance Clock Random输入, 不支持泛型输入

efforts:
1. 升级sui，做相关适配
2. 取package id的方式有问题，只判断了effects是否有create immutable object，事实上freeze_object也会产生这种，加了个判断object data是否为package