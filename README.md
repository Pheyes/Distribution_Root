# Distribution_Root

//Probability distribution for two quanta (assuming both quanta are scattered)
#include "TCanvas.h"
#include "TStyle.h"
#include "TH1.h"
#include "TGaxis.h"
#include "TRandom.h"

void distribution()
{

// dP = [ k1*k1 * k2*k2 * (gamma1**2 - gamma1*sin(theta2)**2 - gamma2*sin(theta1)**2 + 2*sin(theta1)**2*sin(theta2)**2*sin(phi)**2) * dOmega1*dOmega2 ] / [4*pi*pi*k0**4 * (40/9-3*log(3))**2]

//Declarations
 float pi=4*atan(1);

 float theta=0.5*pi;
 float theta1=theta;
 float theta2=theta;

 float k0=2;
 float k1=k0/(2-cos(theta1));
 float k2=k0/(2-cos(theta2));
 
 float gamma1=k1/k0+k0/k1;
 float gamma2=k2/k0+k0/k2;
 //float x;


 TCanvas *c1 = new TCanvas("c1","Distribution",600,400);

 TF1 *f=new TF1("f","([4]**2 * [5]**2 * ([6]**2 - [6]*sin([2])**2 - [7]*sin([1])**2 + 2*sin([1])**2*sin([2])**2*sin(x)**2))/(4*pi*pi*[3]**4 * (40/9-3*log(3))**2)",0,2*pi);

 f->SetParameter(0,theta);
 f->SetParameter(1,theta1);
 f->SetParameter(2,theta2);
 f->SetParameter(3,k0);
 f->SetParameter(4,k1);
 f->SetParameter(5,k2);
 f->SetParameter(6,gamma1);
 f->SetParameter(7,gamma2);
 
 f->Draw();

}

//For reference:

//phi=x
//theta0=p[0]
//theta1=p[1]
//theta2=p[2]
//k0=p[3]
//k1=p[4]
//k2=p[5]
//gamma1=p[6]
//gamma2=p[7]
