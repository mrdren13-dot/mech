
<style>
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: var(--font-sans); }
.container { padding: 1rem 0; }
.header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 1.25rem; flex-wrap: wrap; gap: 8px; }
.header h2 { font-size: 18px; font-weight: 500; color: var(--color-text-primary); }
.copy-all-btn { display: flex; align-items: center; gap: 6px; background: var(--color-background-secondary); border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); padding: 6px 14px; font-size: 13px; font-weight: 500; cursor: pointer; color: var(--color-text-primary); transition: background 0.15s; }
.copy-all-btn:hover { background: var(--color-background-tertiary); }
.program-card { background: var(--color-background-primary); border: 0.5px solid var(--color-border-tertiary); border-radius: var(--border-radius-lg); margin-bottom: 12px; overflow: hidden; }
.card-header { display: flex; align-items: center; justify-content: space-between; padding: 10px 14px; background: var(--color-background-secondary); border-bottom: 0.5px solid var(--color-border-tertiary); cursor: pointer; user-select: none; }
.card-title { display: flex; align-items: center; gap: 10px; }
.prog-num { font-size: 11px; font-weight: 500; background: #E6F1FB; color: #0C447C; padding: 2px 8px; border-radius: 20px; }
.prog-name { font-size: 14px; font-weight: 500; color: var(--color-text-primary); }
.card-actions { display: flex; align-items: center; gap: 8px; }
.copy-btn { display: flex; align-items: center; gap: 5px; font-size: 12px; background: var(--color-background-primary); border: 0.5px solid var(--color-border-secondary); border-radius: var(--border-radius-md); padding: 4px 10px; cursor: pointer; color: var(--color-text-secondary); transition: all 0.15s; white-space: nowrap; }
.copy-btn:hover { background: var(--color-background-info); color: var(--color-text-info); border-color: var(--color-border-info); }
.copy-btn.copied { background: var(--color-background-success); color: var(--color-text-success); border-color: var(--color-border-success); }
.toggle-icon { font-size: 14px; color: var(--color-text-secondary); transition: transform 0.2s; }
.toggle-icon.open { transform: rotate(180deg); }
.code-block { display: none; padding: 14px; background: var(--color-background-tertiary); overflow-x: auto; }
.code-block.open { display: block; }
pre { font-family: var(--font-mono); font-size: 13px; color: var(--color-text-primary); line-height: 1.6; white-space: pre; }
</style>

<div class="container">
  <div class="header">
    <h2><i class="ti ti-code" aria-hidden="true" style="font-size:20px;vertical-align:-2px;margin-right:6px"></i>C Programs</h2>
    <button class="copy-all-btn" onclick="copyAll(this)">
      <i class="ti ti-copy" aria-hidden="true" style="font-size:15px"></i> Copy all programs
    </button>
  </div>
  <div id="programs"></div>
</div>

<script>
const programs = [
  {
    num: "01",
    name: "Celsius to Fahrenheit Conversion",
    code: `#include<stdio.h>
int main()
{
 float deg_cel, deg_fahr;
 printf("\\nEnter the value of tempearture in degree celsius:");
 scanf("%f",&deg_cel);
 deg_fahr = (deg_cel * 9)/5 + 32;
 printf("\\ntemperature in degree fahrenheit:%f",deg_fahr);
 return 0;
}`
  },
  {
    num: "02",
    name: "Quadratic Equation Roots",
    code: `#include<stdio.h>
#include<math.h>
#include<stdlib.h>
int main()
{
float a,b,c;
float d;
float root1,root2;
float real_part, imag_part;
printf("\\nEnter the value of a:");
scanf("%f",&a);
printf("\\nEnter the value of b:");
scanf("%f",&b);
printf("\\nEnter the value of c:");
scanf("%f",&c);
if(a==0)
{
printf("\\nRoots are not possible");
exit(0);
}
d = (b*b)-(4*a*c);
if(d>0)
{
root1 = (-b + sqrt(d))/(2 * a);
root2 = (-b - sqrt(d))/(2 * a);
printf("\\nThe real and distinct roots are:");
printf("\\nThe value of root1:%f",root1);
printf("\\nThe value of root2:%f",root2);
}
else if(d == 0)
{
root1 = root2 = (-b / (2 * a));
printf("\\nThe real and equal roots are:");
printf("\\nThe value of root1:%f",root1);
printf("\\nThe value of root2:%f",root2);
}
else
{
real_part = (-b / (2 * a));
imag_part = sqrt(-d)/(2 * a);
printf("\\nThe complex roots are:");
printf("\\nThe value of root1:%f + i %f",real_part,imag_part);
printf("\\nThe value of root2:%f - i %f",real_part,imag_part);
}
return 0;
}`
  },
  {
    num: "03",
    name: "Prime Number Check",
    code: `#include<stdio.h>
int main()
{
int n,i,c=0;
printf("\\nEnter any number:");
scanf("%d",&n);
for(i=1;i<=n;i++)
{
if(n%i==0)
{
c++;
}
}
if(c==2)
{
printf("Entered number %d is a prime number",n);
}
else
{
printf("Entered number %d is not a prime number",n);
}
return 0;
}`
  },
  {
    num: "04",
    name: "Linear Search in Array",
    code: `#include<stdio.h>
int main()
{
int a[10], i, n, search, found = 0;
printf("Enter the number of elements in the array:");
scanf("%d",&n);
printf("\\nEnter the %d elements:\\n",n);
for(i=0;i<n;i++)
{
scanf("%d",&a[i]);
}
printf("Enter the element to search:");
scanf("%d",&search);
for(i=0;i<n;i++)
{
if(a[i] == search)
{
printf("\\nElement %d is found at index %d",search,i);
found = 1;
}
}
if(found == 0)
{
printf("\\nElement %d is not found in array",search);
}
return 0;
}`
  },
  {
    num: "05",
    name: "Senior Citizen Check",
    code: `#include<stdio.h>
#include<string.h>
int main()
{
int age, result;
char str[50];
printf("\\nEnter the age of a person:");
scanf("%d", &age);
printf("\\nEnter the gender of a person:");
scanf("%s",str);
if(age>=60)
{
if(strcmp(str,"male") == 0)
{
printf("\\nPerson is a male senior citizen");
}
else
{
printf("\\nPerson is a female senior citizen");
}
}
else
{
printf("\\nPerson is not a senior citizen");
}
return 0;
}`
  },
  {
    num: "06",
    name: "Number Triangle Pattern",
    code: `#include<stdio.h>
int main()
{
int i,j,n,sum=0;
printf("Enter the number of rows:");
scanf("%d",&n);
for(i=1;i<=n;i++)
{
for(j=1;j<=i;j++)
{
sum = sum + 1;
printf("%d ",sum);
}
printf("\\n");
}
return 0;
}`
  },
  {
    num: "07",
    name: "Matrix Transpose",
    code: `#include<stdio.h>
int main()
{
int a[10][10], b[10][10], i, j;
int rows,columns;
printf("Enter the number of rows and columns of matrix:\\n");
scanf("%d%d",&rows,&columns);
printf("\\nEnter the elements of matrix:\\n");
for(i=0;i<rows;i++)
{
for(j=0;j<=columns-1;j++)
{
scanf("%d",&a[i][j]);
}
printf("\\n");
}
for(i=0;i<rows;i++)
{
for(j=0;j<columns;j++)
{
b[j][i]= a[i][j];
}
}
printf("Transpose of matrix is :\\n");
for(i=0;i<columns;i++)
{
for(j=0;j<rows;j++)
{
printf("%d ",b[i][j]);
}
printf("\\n");
}
return 0;
}`
  },
  {
    num: "08",
    name: "String Operations (concat, length, copy)",
    code: `#include<stdio.h>
#include<string.h>
int main()
{
char source1[50];
char source2[50];
char destination[50];
printf("\\nEnter a first string:");
scanf("%s", source1);
printf("\\nEnter a second string:");
scanf("%s", source2);
strcat(source1,source2);
printf("\\nConcatenated string: %s", source1);
printf("\\nlength of string:%lu",strlen(source1));
strcpy(destination, source1);
printf("\\nCopied string:%s",destination);
return 0;
}`
  },
  {
    num: "09",
    name: "GCD and LCM",
    code: `#include<stdio.h>
int gcd(int num, int den)
{
int r;
r = num % den;
while (r !=0)
{
num = den;
den = r;
r = num % den;
}
return den;
}
int lcm(int n1,int n2,int gcd)
{
int result = (n1 * n2)/gcd;
return result;
}
int main()
{
int num1, num2, numerator, denominator, rem=0, GCD, LCM;
printf("\\nEnter the first number:");
scanf("%d",&num1);
printf("\\nEnter the second number:");
scanf("%d",&num2);
if(num1 > num2)
{
numerator = num1;
denominator = num2;
}else
{
numerator = num2;
denominator = num1;
}
GCD = gcd(numerator,denominator);
printf("\\nThe gcd of two numbers is:%d", GCD);
LCM = lcm(numerator,denominator,GCD);
printf("\\nThe lcm of two numbers is:%d", LCM);
return 0;
}`
  },
  {
    num: "10",
    name: "Employee Salary Comparison (Struct)",
    code: `#include<stdio.h>
#include<string.h>
struct employees{
char name[50];
int ID;
int salary;
};
int main()
{
struct employees employee1;
struct employees employee2;
printf("\\nEnter the details of the employee1:\\n");
printf("Enter the name of the employee1:");
scanf("%s",employee1.name);
printf("Enter the employee1 ID:");
scanf("%d",&employee1.ID);
printf("Enter the employee1 salary:");
scanf("%d",&employee1.salary);
printf("\\nEnter the details of the employee2:\\n");
printf("Enter the name of the employee2:");
scanf("%s",employee2.name);
printf("Enter the employee2 ID:");
scanf("%d",&employee2.ID);
printf("Enter the employee2 salary:");
scanf("%d",&employee2.salary);
printf("\\nEmployee having the Higher salary:\\n");
if(employee1.salary > employee2.salary)
{
printf("\\nName:%s\\n",employee1.name);
printf("ID: %d\\n",employee1.ID);
printf("Salary:%d\\n",employee1.salary);
}
else if(employee2.salary > employee1.salary)
{
printf("\\nName:%s\\n",employee2.name);
printf("ID: %d\\n",employee2.ID);
printf("Salary:%d\\n",employee2.salary);
}
else
{
printf("\\nBoth the employees have the same salary\\n");
printf("\\nName:%s\\n",employee1.name);
printf("ID: %d\\n",employee1.ID);
printf("Salary:%d\\n",employee1.salary);
printf("\\nName:%s\\n",employee2.name);
printf("ID: %d\\n",employee2.ID);
printf("Salary:%d\\n",employee2.salary);
}
return 0;
}`
  },
  {
    num: "11",
    name: "Sum Using Pointers",
    code: `#include<stdio.h>
int main()
{
int num1, num2, sum=0;
int *ptr1, *ptr2;
ptr1 = &num1;
ptr2 = &num2;
printf("Enter the first number:");
scanf("%d",ptr1);
printf("\\nEnter the second number:");
scanf("%d",ptr2);
sum = *ptr1 + *ptr2;
printf("\\nThe sum of %d and %d is %d", *ptr1, *ptr2, sum);
return 0;
}`
  },
  {
    num: "12",
    name: "Sum of Digits",
    code: `#include<stdio.h>
int main()
{
int number, sumofdigits = 0, rem = 0, quotient;
printf("Enter the number:");
scanf("%d",&number);
quotient = number;
while(quotient != 0)
{
rem = number % 10;
sumofdigits = sumofdigits + rem;
quotient = number / 10;
number = quotient;
}
printf("the sum of digits of a number is: %d",sumofdigits);
return 0;
}`
  },
  {
    num: "13",
    name: "Matrix Multiplication",
    code: `#include <stdio.h>
#include <stdlib.h>
void main()
{
int m, n, p, q, i, j, k, a[10][10], b[10][10], c[10][10];
printf("Enter the order of matrix A ");
scanf("%d%d", &m, &n);
printf("Enter the order of matrix B ");
scanf("%d%d", &p, &q);
if (n != p){
printf("Matrix multiplication is not possible\\n");
exit(0);
}
printf("Enter elements to matrix A\\n");
for (i = 0; i < m; i++)
{
for (j = 0; j < n; j++)
{
scanf("%d", &a[i][j]);
}
}
printf("Enter elements to matrix B\\n");
for (i = 0; i < p; i++)
{
for (j = 0; j < q; j++)
{
scanf("%d", &b[i][j]);
}
}
for (i = 0; i < m; i++)
{
for (j = 0; j < q; j++)
{
c[i][j] = 0;
for (k = 0; k < n; k++)
{
c[i][j] = c[i][j] + a[i][k] * b[k][j];
}
}
}
printf("The matrix A\\n");
for (i = 0; i < m; i++)
{
for (j = 0; j < n; j++)
printf("%d\\t", a[i][j]);
printf("\\n");
}
printf("The matrix B\\n");
for (i = 0; i < p; i++)
{
for (j = 0; j < q; j++)
{
printf("%d\\t", b[i][j]);
}
printf("\\n");
}
printf("The Resultant matrix C\\n");
for (i = 0; i < m; i++)
{
for (j = 0; j < q; j++)
{
printf("%d\\t", c[i][j]);
}
printf("\\n");
}
}`
  },
  {
    num: "14",
    name: "Book Search Using Struct",
    code: `#include<stdio.h>
#include<string.h>
#include<stdlib.h>
struct book {
char title[100];
char author[100];
int pages;
float price;
};
int main()
{
struct book b[2];
int i, found = 0;
char bookname[100];
strcpy(b[0].title,"programming in ansi c");
strcpy(b[0].author,"e balaguruswamy ");
b[0].pages = 596;
b[0].price = 595;
strcpy(b[1].title,"programming in c");
strcpy(b[1].author,"reema thareja ");
b[1].pages = 468;
b[1].price = 550;
printf("\\n");
printf("Enter the name of the book:");
fgets(bookname, sizeof(bookname), stdin);
bookname[strcspn(bookname,"\\n")] = 0;
for (i=0;i<2;i++)
{
if (strcmp(bookname,b[i].title) == 0)
{
printf("Book is available\\n");
printf("\\nName of the book:%s",b[i].title);
printf("\\nAuthor of the book:%s",b[i].author);
printf("\\nNumber of pages in the book:%d",b[i].pages);
printf("\\nPrice of the book:%f\\n",b[i].price);
exit(0);
}
found++;
}
if(found != 0)
{
printf("\\nBook is not available");
}
return 0;
}`
  }
];

function escapeHtml(str) {
  return str.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function copyCode(btn, code) {
  navigator.clipboard.writeText(code).then(() => {
    btn.classList.add('copied');
    btn.innerHTML = '<i class="ti ti-check" aria-hidden="true" style="font-size:13px"></i> Copied!';
    setTimeout(() => {
      btn.classList.remove('copied');
      btn.innerHTML = '<i class="ti ti-copy" aria-hidden="true" style="font-size:13px"></i> Copy';
    }, 1800);
  });
}

function copyAll(btn) {
  const all = programs.map((p, i) => `/* Program ${p.num}: ${p.name} */\n${p.code}`).join('\n\n/* ==================== */\n\n');
  navigator.clipboard.writeText(all).then(() => {
    btn.innerHTML = '<i class="ti ti-check" aria-hidden="true" style="font-size:15px"></i> Copied all!';
    setTimeout(() => {
      btn.innerHTML = '<i class="ti ti-copy" aria-hidden="true" style="font-size:15px"></i> Copy all programs';
    }, 2000);
  });
}

function toggleCard(idx) {
  const block = document.getElementById('code-' + idx);
  const icon = document.getElementById('icon-' + idx);
  block.classList.toggle('open');
  icon.classList.toggle('open');
}

const container = document.getElementById('programs');
programs.forEach((p, i) => {
  const card = document.createElement('div');
  card.className = 'program-card';
  card.innerHTML = `
    <div class="card-header" onclick="toggleCard(${i})">
      <div class="card-title">
        <span class="prog-num">${p.num}</span>
        <span class="prog-name">${p.name}</span>
      </div>
      <div class="card-actions" onclick="event.stopPropagation()">
        <button class="copy-btn" onclick="copyCode(this, programs[${i}].code)">
          <i class="ti ti-copy" aria-hidden="true" style="font-size:13px"></i> Copy
        </button>
        <i class="ti ti-chevron-down toggle-icon" id="icon-${i}" aria-hidden="true" onclick="event.stopPropagation(); toggleCard(${i})"></i>
      </div>
    </div>
    <div class="code-block" id="code-${i}">
      <pre>${escapeHtml(p.code)}</pre>
    </div>
  `;
  container.appendChild(card);
});
</script>
