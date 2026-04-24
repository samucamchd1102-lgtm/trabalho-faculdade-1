[trabalho.c](https://github.com/user-attachments/files/27068672/trabalho.c)
/*
=========================================================
PROGRAMA: RESOLVEDOR DE EQUACOES DO 1o E 2o GRAU
PADRAO : ANSI C
=========================================================
*/

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

/* Prot�tipos */
void menu();
void primeiroGrau();
void segundoGrau();
void sobrePrograma();
void pausar();

int main()
{
    int opcao;

    do
    {
        menu();
        printf("\nEscolha uma opcao: ");
        scanf("%d",&opcao);

        switch(opcao)
        {
            case 1:
                primeiroGrau();
                break;

            case 2:
                segundoGrau();
                break;

            case 3:
                sobrePrograma();
                break;

            case 0:
                printf("\nEncerrando o programa...\n");
                break;

            default:
                printf("\nOpcao invalida!\n");
        }

    } while(opcao != 0);

    return 0;
}

/* Menu principal */
void menu()
{
    printf("\n=====================================\n");
    printf("   RESOLVEDOR DE EQUACOES\n");
    printf("=====================================\n");
    printf("1 - Equacao do 1o Grau\n");
    printf("2 - Equacao do 2o Grau\n");
    printf("3 - Sobre o Programa\n");
    printf("0 - Sair\n");
    printf("=====================================\n");
}

/* Equa��o do 1� grau: ax + b = 0 */
void primeiroGrau()
{
    float a,b,x;

    printf("\n--- EQUACAO DO 1o GRAU ---\n");
    printf("Forma geral: ax + b = 0\n\n");

    printf("Digite o valor de a: ");
    scanf("%f",&a);

    printf("Digite o valor de b: ");
    scanf("%f",&b);

    printf("\nPASSO A PASSO:\n");
    printf("--------------------------------\n");

    printf("Equacao original:\n");
    printf("%.2fx + %.2f = 0\n\n",a,b);

    if(a==0)
    {
        if(b==0)
            printf("Infinitas solucoes.\n");
        else
            printf("Equacao impossivel.\n");

        pausar();
        return;
    }

    printf("1) Isolando x:\n");
    printf("%.2fx = -(%.2f)\n",a,b);
    printf("%.2fx = %.2f\n\n",a,-b);

    printf("2) Dividindo por %.2f:\n",a);
    printf("x = %.2f / %.2f\n\n",-b,a);

    x=-b/a;

    printf("3) Solucao:\n");
    printf("x = %.2f\n",x);

    pausar();
}

/* Equa��o do 2� grau: ax� + bx + c = 0 */
void segundoGrau()
{
    float a,b,c;
    float delta,x1,x2;

    printf("\n--- EQUACAO DO 2o GRAU ---\n");

    printf("Digite a: ");
    scanf("%f",&a);

    printf("Digite b: ");
    scanf("%f",&b);

    printf("Digite c: ");
    scanf("%f",&c);

    if(a==0)
    {
        printf("\nNao e equacao do 2o grau.\n");
        pausar();
        return;
    }

    printf("\nPASSO A PASSO:\n");
    printf("--------------------------------\n");

    printf("Equacao:\n");
    printf("%.2fx� + %.2fx + %.2f = 0\n\n",a,b,c);

    printf("Formula de Bhaskara:\n");
    printf("x = (-b +- raiz(delta))/2a\n\n");

    printf("1) Calculando delta:\n");
    printf("delta = b� - 4ac\n");

    delta = (b*b) - (4*a*c);

    printf("delta = (%.2f)� -4(%.2f)(%.2f)\n",b,a,c);
    printf("delta = %.2f\n\n",delta);

    if(delta < 0)
    {
        printf("Nao existem raizes reais.\n");
        pausar();
        return;
    }

    if(delta == 0)
    {
        x1 = (-b)/(2*a);

        printf("Raiz dupla:\n");
        printf("x = %.2f\n",x1);

        pausar();
        return;
    }

    x1=(-b + sqrt(delta))/(2*a);
    x2=(-b - sqrt(delta))/(2*a);

    printf("2) Calculando raizes:\n");
    printf("x1 = %.2f\n",x1);
    printf("x2 = %.2f\n",x2);

    pausar();
}

/* Sobre o programa */
void sobrePrograma()
{
    printf("\n================================\n");
    printf("        SOBRE O PROGRAMA\n");
    printf("================================\n");

    printf("Sistema: Resolvedor de Equacoes\n");
    printf("Desenvolvido por:\n");
    printf("- Aluno 1: Samuel Machado Carvalho\n");
    printf("- Aluno 2: Gabriel Dutra\n");
    printf("- Aluno 3: Pedro Henrique Lopes\n");
    printf("- Institui��o: Centro Universit�rio Avantis 2026")
    printf("\nVersao 1.0 - ANSI C\n");

    pausar();
}

/* Pausa */
void pausar()
{
    printf("\nPressione ENTER para continuar...");
    getchar();
    getchar();
}
