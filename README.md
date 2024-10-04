% Reaction rates in 1/sec
k1=2; 
k2=2;
k3=2;
k4=2;

% Defined constraints of the complication
% a=1;
b=k1+k2+k3+k4
c=(k1*k3)+(k2*k4)+(k4*k1);
d=k2*k4;
f=k3+k2+k4;

r1=(-b-sqrt(b^2-4*a*c))/2*a;
r2=(-b+sqrt(b^2-4*a*c))/2*a;
c2=(1-(d/c)+(k1/r1))/(1-(r2/r1));
c1=(-k1/r1)-(r2/r1)*c2;
c3=(-k4/f);

% Time Vector
% t=0:0.01:5;

% Molar Concentration versus time
Na=c1*exp(r1.*t)+c2*exp(r2.*t)+(d/c);
Nr=((r1*c1*exp(r1.*t))+(r2*(c2*exp(r2.*t)))+(k1*(c1*exp(r1.*t)+c2*exp(r2.*t)+(d/c))))/k2;
Ns=1-Na-Nr;

plot(t,Na)
hold on

plot(t,Nr)
plot(t,Ns)

title( "Molar Concentration for A,R and S")
ylabel('Moles (N)')
xlabel('time (sec)')
legend('Na','Nr','Ns')
hold off
