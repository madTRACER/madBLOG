---
title: 'Errors Counter'
description: 'In the beginning of my education year I quickly wrote simple program which calculates Standard Deviation , Absolute and Relative errors automatically. You can get it from my GitLab (link is below) and adapt it for your needs.'
date: '2018-11-29T20:29:05+06:00'
template: 'post'
draft: false
slug: 'errors-counter'
category: 'QuickFix'
tags: ['C++', 'Linux', 'QuickFix']
socialImage: '/media/2018-11-29--quickfix.png'
---
![](/media/2018-11-29--quickfix.png)

In the beginning of my education year I quickly wrote simple program which calculates Standard Deviation , Absolute and Relative errors automatically. You can get it from my GitLab (link is below) and adapt it for your needs.

Lets consider it in detail…

I created a class **Measurements***. Then I created all needed variables (commented in code) and methods.

```c++
class Measurements{
private:
	double sc = 2.78; //student coefficient
	double sd; //std deviation value
	double ae; //absolute err value
	double re; //relative err value
public:
	double std_dev(double m1,double m2,double m3,double m4,double m5){
		double sq_sum = (m1*m1)+(m2*m2)+(m3*m3)+(m4*m4)+(m5*m5);
		sd = sqrt(sq_sum/20);
		return sd;
	}
	double abs_err(){
		ae = sd*sc;
		return ae;
	}
	double rel_err(double am){ //am need arithmetic mean value
		re = ae/am;
		return re;
	}
};
```

As you can see, **std\_dev** method calculates Standard Deviation for 5 measurements only, but I remind you that it was written as QuickFix program. **abs\_err** method finds absolute error and **rel\_err** method obviously calculates relative error.

After this part of code the program has very simple **main** function, which is so simple to understand, as I think.

<https://gitlab.com/madTRACER/errorscounter>