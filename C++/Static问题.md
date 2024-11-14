
#### 在类和结构体外的情况
##### 全局情况
###### 针对单个文件的”私有可视化“
如果static某个变量或某个函数，实际上就是说这个变量或函数只会在本文件内可见和使用。

在文件被编译和链接的时候，static变量不会被链接到其他文件。

如果两个文件分别有同名的变量，编译时一定会报错，其中一个有static关键字则不会。

或者其中一个变量用extern 关键字，意思是本变量的定义要从其他文件中寻找与同一。或者说变量的公有可视化。（全局变量）

##### 局部静态情况

#### 在类和结构体内的情况
##### static 变量的情况
下面我们采用struct来举例
```
struct Entity
{
	static int x, y;
	
	static void Print()
	{
		std::cout << x << " " << y << std::endl;
	}



	/*static void Print(Entity e)
	{
		std::cout << e.x << " " << e.y << std::endl;
	}*/
};

int Entity::x;
int Entity::y;
int main()
{
	Entity e1;
	Entity e2;
	Entity::Print(e1);
	std::cin.get();
}
```
如果我们在class或struct中static一个变量，这意味着这个变量是这种class或struct关键字的共用变量，以上图为例子，我们设置名为Entity的结构体，在Entity中设置静态变量x和y。