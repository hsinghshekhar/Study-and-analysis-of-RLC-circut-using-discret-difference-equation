RL Circuit Modelling through Finite Difference Approximation- During my MSc(IISER-TVM, Kerela) 3rd semester 2023, i enrolled in subject called "Numerical Solution of Differential Equation". I study and learn and also learn to implement how differetial equation and partial differential equation is changed into Finite Difference Approximation with aid of finite difference scheme, centred difference scheme,etc.

Recently i enrolled a course "EXCELing with Mathematical Modeling" in 2024 on NPTEL by Prof. SANDIP BANERJEE a Professor in the Department of Mathematics, Indian Institute of Technology Roorkee (IITR), India. There is one mathematical model introduce that is Discrete Models. With the help of Finite Difference scheme, we try to learn better the dynamics of RL cricut with help of mathematical equation. And this concept are comes in my mind during study of Discrete Models in the course EXCELing with Mathematical Modeling.

This model is one of the parts of numerically approach

![Screenshot 2024-09-24 173413](https://github.com/user-attachments/assets/bc58d60b-a3aa-48d2-afef-66de71c62577) 

Introduction-In most electrical programs, after introducing basic elements of Ohm’s and Kirchhoff’s current and voltage laws, the dynamic response of the circuits containing capacitors and inductors will be studied. solving the differential equations, and understanding the dynamic response of circuits. To improve students’ understanding, Hence, we propose a novel approach for these circuit analyses through the application of a discretized version of differential equations which i used in these circuit. The analysis can be performed by hand or this is also helpful for those who prefer modern education aided by computers. Approximation of differential equations by difference equations is useful for cases in which a close-form solution is not possible to be obtained for differential equations. We denote $y'(x)$ in finite difference method is 

![Screenshot 2024-09-24 204209](https://github.com/user-attachments/assets/f226e8f7-a9ad-4929-8214-119a8c0ad072)

where ∆𝑡 should be chosen as small as possible, and k is discrete time. Now, Voltage across $L$ is $\frac{Ld I}{d t}$ and voltage across resistor is $R I$. Total voltage in loop is 

$V=R I(t)+L \frac{d I(t)}{d t}$, 

by solving the above equation, we get $I(t)=\frac{V}{R}\left(1-e^{\frac{-R t}{L}}\right)$. now, by Finite difference approximation. our, discret the domain $(0, T)$ into mess point, where $T>0$ is the finite time. let $\Delta t$ = time step, $t_k=k \Delta t, k=0,1,2, M$ be the mass point. Let $I(t _k)$ be the solution, and this denote in finite difference approximation is

$$\frac{d I\left(t_{k})\right.}{d t}=\frac{I\left(t_{m+1}\right)-I\left(t_m\right)}{\Delta t}$$

now, the above equation in discrete difference form in time 
space $(0,T)$ is

$$
\begin{aligned}
&  V(k)=R I(k)+L\left[\frac{I(t_{k+1})-I(t_k)}{\Delta t}\right] \\
& \text {} \\
& V(k)=R I(k)+\frac{L}{\Delta t}[I(k+1)-I(k)] \\
& \text { } I(k+1)=\left(1-\frac{R \Delta t}{L}\right) I(k)+\frac{\Delta t}{L} V(k)
\end{aligned}
$$

our difference equation in time-space $T>0$ and  $m=0,1,2, \ldots, M$ 

This is also called the recurrence relation of the RL circuit because the next value is dependent on the previous value.

Note: $\left(1-\frac{R \Delta t}{L}\right) ,\frac{\Delta t}{L}$ is dimensionless
number. 

$$
\begin{aligned}
& I_k=\left(1-\frac{R A t}{L}\right) I_{k-1}+\frac{\Delta t}{L} V_{k-1} \\
& I_{k+1}=\left(1-\frac{R \Delta t}{L}\right)\left[\left(1-\frac{R \Delta t}{L}\right) I_{k-1}+\frac{\Delta t}{L} V_{k-1}\right]+ \\ \frac{\Delta t}{L} V_k \\
\end{aligned}$$

$$\begin{aligned}
& I_{k+1}=\left(1-\frac{R \Delta t}{L}\right)^2 I_{k-1}+\frac{\Delta t}{L}\left(1-\frac{R \Delta t}{L}\right) V_{k-1}+\frac{\Delta t}{L} \mathrm{V_k} \\
& \left.=\left(1-\frac{R \Delta t}{L}\right)^2\left[(1-\frac{R \Delta t}{L}\right) I_{k-2}+\frac{\Delta t}{L} V_{k-2}\right]+ \\& \frac{\Delta t}{L}\left(1+\frac{R \Delta t}{L}\right) V_{k-1}+\frac{\Delta t}{L} V_k \\
\end{aligned}$$

$$
\begin{aligned}
& =\left(1-\frac{R \Delta t}{L}\right)^3 I_{k-2}+\left(1-\frac{R \Delta t}{L}\right)^2 \frac{\Delta t}{L} V_{m-2}+ \\& \frac{\Delta t}{L}\left(1-\frac{R \Delta t}{L}\right) V_{k-1}+\frac{\Delta t}{L} V_{k-0} \\
\end{aligned}$$

$$
\begin{aligned}
& I_{k+1}=\left(1-\frac{R \Delta t}{L}\right)^3\left[\left(1-\frac{R \Delta t}{L}\right) I_{k-3}+\frac{\Delta t}{L} V_{k-3}\right] \\& +\left(1-\frac{R \Delta t}{L}\right)^2 \frac{\Delta t}{L} V_{k-2}+\frac{\Delta t}{L}\left(1-\frac{R \Delta t}{L}\right) V_{k-1}+ \frac{\Delta t}{L}V_k \\
\end{aligned}$$

$$
\begin{aligned}
& I_{k+1}=\left(1-\frac{R \Delta t}{L}\right)^{k+1} I_0+\frac{\Delta t}{L} \sum_{i=0}^k\left(1-\frac{R \Delta t}{L}\right)^k V_{k-i}
\end{aligned}$$

where $k=0,1,2, \ldots, M$

The solution $I_{k+1}$ is the discrete form of a solution of the RL circuit.
This observation and analysis are not easily possible via direct 
solution of the differential equation. Moreover, the students 
can easily code this procedure using any programming code. As an example, am using code written in
MATLAB, I also attach code and graph. Nothing changed in the graph, but you can see it in the discrete signal.

Ex- $V = sin(2*pi*50*k*dt)$ a 50 Hz sinusoidal input, voltage source, Voltage function, you can change this as needed,
$R = 0.001$; Resistance in ohms and is a current sense resistor, $L = 0.000001$; % Inductance in Henries, however, the best inductor value depends on the application, $1.0 µH$: Often used in high-frequency applications, $dt = 0.001$; time step in seconds.

![Screenshot 2024-09-26 200354](https://github.com/user-attachments/assets/ac8a810b-6f71-4dc8-9123-d51a29f9589a)

I set up all this, and then I got a current of $1000$ amplitude.
Now, class 12th students can relate to this, analyse phase shift and amplitude, and understand them better using a mathematical approach.

After all this, I personally took for granted studying RLC circuits for stability/stable(because an Unstable circuit causes damage to
electrical systems) and bounded graph of current, this is only a introduction part.

