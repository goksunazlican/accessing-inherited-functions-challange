# accessing-inherited-functions-challange
In class A, func multiplies the value passed as a parameter by 2,
In class B, func multiplies the value passed as a parameter by 3,
In class C, func multiplies the value passed as a parameter by 5.

given class A definition:
```cpp
class A
{
    public:
        A(){
            callA = 0;
        }
    private:
        int callA;
        void inc(){
            callA++;
        }

    protected:
        void func(int & a)
        {
            a = a * 2;
            inc();
        }
    public:
        int getA(){
            return callA;
        }
}
```

given class B definition:
```cpp
class B
{
    public:
        B(){
            callB = 0;
        }
    private:
        int callB;
        void inc(){
            callB++;
        }
    protected:
        void func(int & a)
        {
            a = a * 3;
            inc();
        }
    public:
        int getB(){
            return callB;
        }
};
```
given class C definition:
```cpp
class C
{
    public:
        C(){
            callC = 0;
        }
    private:
        int callC;
        void inc(){
            callC++;
        }
    protected:
        void func(int & a)
        {
            a = a * 5;
            inc();
        }
    public:
        int getC(){
            return callC;
        }
};
```

Class D created to find out how many times the functions of A, B, and C are called to generate the given number:

Firstly, class D should be inherited from A, B, and C for accessing the protected functions.
```cpp
class D: public A, public B, public C 
{

	int val;
	public:
		//Initially val is 1
		 D()
		 {
		 	val = 1;
		 }
```
In `update_val()`, I used while loops to find out exactly how many times new_value divided by 2,3 and 5.
Accessing the protected `func()`, i.e. **A::func(val)**.
```cpp
		 void update_val(int new_val)
		 {
		 	while(new_val%2==0){
		 		A::func(val); 		
		 		new_val/=2;
		 	}

		 	while(new_val%3==0){
		 		B::func(val);
		 		new_val/=3;
		 	}

		 	while(new_val%5==0){
		 		C::func(val);
		 		new_val/=5;
		 	}

		 }
		 //For Checking Purpose
		 void check(int); //Do not delete this line.
};
```
