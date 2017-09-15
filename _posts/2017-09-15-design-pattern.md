---
layout: post
title: "design pattern"
description: "design pattern example"
date: 2017-09-15
tags: [design pattern, decorator pattern]
comments: false
share: false
---

온라인 강의로 들었던 예제

---

## 1. Decorator Pattern

* 시작

``` cpp
class Picture {
	string imgsrc;
    public:
    void Draw(){cout<<"picture draw"<<endl; }
};

class DrawFrame : public Picture  {
	public:
	void Draw(){
		Picture::Draw();
		cout<<"Frame draw"<<endl;
	}
};

int main()
{
	Picture pic;
	pic.Draw();

	DrawFrame frame;
	frame.Draw();
	return 0;
}
```

* 첫번째 

``` cpp
#include <iostream>
#include <string>

using namespace std;

class Picture {
public:
	void Draw(){cout<<"Picture draw"<<endl;}
};

class FrameDecorator {
private:
		Picture* pic;
public:
	FrameDecorator(Picture* p) : pic(p){}
	void Draw(){
		pic->Draw();
		cout<<"Frame draw"<<endl;
	}
};

int main()
{
	Picture pic;
	pic.Draw();
	FrameDecorator fd(&pic);
	fd.Draw();
	return 0;
}

```


* 두번째

```cpp
struct Item {
	virtual void Draw()=0;
	virtual ~Item()=default;
};

class Picture : public Item {
	string name;
	public:
	void Draw(){ cout<<"Picture draw"<<endl;}
};

class FrameDecorator : public Item {
	Item* pic;
public:
	FrameDecorator(Item* p) : pic(p){}
	void Draw(){
	cout<<"frame draw"<<endl;
	}
};

class FlowerDecorator : public Item {
	Item* pic;
public:
	FlowerDecorator(Item* p) : pic(p){}
	void Draw(){
		cout<<"flower draw"<<endl;
	}
};

int main()
{
    Picture pic;
    FrameDecorator fd(&pic);
    FlowerDecorator fd2(&pic);
    fd2.Draw();
}

```
* 세번째

```cpp
struct Item {
    virtual void Draw()=0;
    virtual ~Item()=default;
};

class Picture : public Item {
    public:
        void Draw() override final {
            cout<<"picture draw"<<endl;
        }
};

class IDecorator : public Item {
    Item* pic;
    public:
    IDecorator(Item *p) : pic(p){}
    void Draw() { pic->Draw();}
};

class FrameDecorator : public IDecorator {
    public:
      FrameDecorator(Item* p) : IDecorator(p){}

      void Draw(){
          IDecorator::Draw();
          cout<<"Draw frame"<<endl;
      }
};

class FlowerDecorator : public IDecorator {
    public:
        FlowerDecorator(Item* p) : IDecorator(p){}
        void Draw() {
            IDecorator::Draw();
            cout<<"Draw flower"<<endl;
        }
};

int main()
{
    Picture pic;
    FrameDecorator fd(&pic);
    FlowerDecorator fd2(&pic);
    fd2.Draw();
	return 0;
}
```

