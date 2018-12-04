# Survival Analysis
---
# Motivation (1) 

* Using the information of time-to-event instead of using only event/non event information
* 

Picture of censored data

---
# Motivation (2) 

Table of data


---
# Censoring 

An observation is said to be censored if event does not happen during the observation period. 

Different type of censoring might occur: 
- left censoring: $T>T_i$ 
- right censoring: $T>T_i$ 
- interval censoring: $T_i<T<T_j$

&double check left censoring&

---
# How to estimate the survival function?

We can estimate the survival function using *Kaplan-Meier* estimator

$$ 
S(t) = \Pi_{i:t_i \le t} \big(1-\frac{d_i}{n_i})
$$

Where $d_i$ and $n_i$ respectively denotes the number of events and the total individuals at risk at time $t_i$

---
$$
\begin{aligned}
	x &= y \\
      &= x^2 + y \\
\end{aligned}
$$

---

## Basic of Survival Model 

- Survival at time $t$ is denoted by $S(t):=P(T>t)$  
- The instantaneous default at time $t$ is modelled as    
   
   $h(t)$ is often called hazard rate. 
   
  $$
  \begin{aligned}
	  h(t)dt &= P(t \lt T \lt t+dt | T>t) \\
             &= -\frac{dS(t)}{S(t)} \\ 
             &= -\frac{f(t)}{S(t)} \\
  \end{aligned}
  $$
---
# Survival Function and Hazard Rate

Probability of survival up to time $t$
$$ S(t) := P(T>t) $$
Where $T$ is a random variable which denotes the time of death. 


---
# None 
Knowing either one of hazard function, survival function, or cumulative hazard function allows us to derive the others

$$
\begin{matrix}
H(t) &= & \int_0^th(s) ds \\
S(t) &= & e^{-H(t)} \\
h(t) &= & -\frac{d\ln{S(t)}}{dt}
\end{matrix}
$$

**use begin align for deriving equation** and marp uses mathjax 

--- 
# How are the parameters being estimated? (1)
The parameters $\theta$ of a survival function $S(T_i|\theta)$ are estimated using the following likelihood: 

$$
L(\theta) = L^{u.c}(\theta)\times L^{l.c} (\theta) \times L^{r.c.} (\theta) \times L^{i.c}(\theta)
$$

Where $L^{u.c}$,$L^{r.c}$,$L^{l.c.}$,$L^{i.c.}$ respectively denote likelihood functions of uncensored, right censored, left censored, and interval censored observations.

---
# How are the parameters being estimated? (2)

$L^{u.c.}$,$L^{r.c.}$,$L^{l.c.}$,$L^{i.c.}$ can be broken down as follows: 


$$
\begin{matrix}
L^{u.c.} (\theta) &=  \Pi_{i \in u.c.}P(T=T_i|\theta) &= f(T_i|\theta) \\

L^{l.c.} (\theta) &=  \Pi_{ i \in l.c. }P(T<T_i|\theta) &= \Pi_{ i \in l.c. }\big(1-S(T_i|\theta)\big) \\

L^{r.c.} (\theta) &=  \Pi_{ i \in r.c. } P(T>T_i|\theta) &= \Pi_{ i \in r.c. } S(T_i|\theta) \\

L^{i.c.} (\theta) &=  \Pi_{i \in i.c.} P( T_i<T<T_j | \theta) &= \Pi_{i \in i.c.} (-S(T_j|\theta)+S(T_i|\theta)\\

\end{matrix}
$$




---
## Accelerated Failure Time 
Accelerated failure time model can be specified as 
$$ h(t|\theta) = \theta \lambda_0(\theta t)$$
Where $\theta$ acts as joint covariate effects whose functional form can be specified parametrically.  
The consequence of this is that 
$$ S(t|\theta) = S_0 (\theta t)$$
The generic functional form of $\theta$ can be chosen according to the data. For example 
$$ \theta = \exp(-\beta X) $$ 
can be chosen.  

---
# Appendix 
---
# Deriving Kaplan-Meier

In a discrete cases
$$
S(t) = \Pi_{i:t_i \le t} (1-h_i)
$$

At time $t_j$ suppose that there are $d_j$ events out of $n_j$ subjects at risk. Their likelihood at $t_j$ is given by 
$$
\begin{aligned}
    L(h_{j:j \le i} | d_{j:j \le i}, n_{j:j \le i})   &= \Pi_{j: j \le i} h_j^{d_j}(1-h_j)^{n_j-d_j} 
\end{aligned}

$$

Maximizing this likelihood, i.e. by setting the derivatives w.r.t. $h_j$ to be equal to zero will give us 
$$
	S(t) = \Pi_{i:t_i \le t} (1-\frac{d_i}{n_i})
	
$$


