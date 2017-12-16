# Furier-Fingerprints-Graphic


#include "txlib.h"

int const FUNCTION_SIZE = 200;

void graphic ( double x[], double y[], int x0, int y0);

int main ()

    {

    txCreateWindow ( 1100, 650);
    double datax[FUNCTION_SIZE] = {};
    double datay[FUNCTION_SIZE] = {};
    for (int i = 0; i < FUNCTION_SIZE; i++)

        {

        datax[i] = i;
        datay[i] = i*i;

        }

    graphic ( datax, datay, 50, 625);

    }


void graphic ( double x[], double y[], int x0, int y0)

    {

    int graphic_leny = 600;
    int graphic_lenx = 1000;
    txSetColor (TX_WHITE, 2);

    txSetFillColor (TX_WHITE);
    txSelectFont ("Comic Sans MS", 16.18, 10);
    double biggesty = y[0];
    double zoom = 1;

    for (int i = 1; i < FUNCTION_SIZE; i++)

        {

        if (biggesty < y[i]) biggesty = y[i];

        }

    double zoomy = 580/biggesty;
    double zoomx = 950/x[FUNCTION_SIZE - 1];
    printf ("zoomx = %f — zoomy = %f\n ", zoomx, zoomy);


    while ( 1 > 0 )

        {

        txSetColor (TX_WHITE);
        txSetFillColor (TX_WHITE);
        txLine ( x0, y0 - graphic_leny * zoom, x0, y0);
        txLine ( x0, y0 - graphic_leny * zoom, x0 + 10, y0 - graphic_leny * zoom + 10);
        txLine ( x0, y0 - graphic_leny * zoom, x0 - 10, y0 - graphic_leny * zoom + 10);
        txLine ( x0, y0, x0 + graphic_lenx * zoom, y0);
        txLine ( x0 + graphic_lenx * zoom, y0, x0 + graphic_lenx * zoom - 10, y0 - 10);
        txLine (x0 + graphic_lenx * zoom , y0, x0 + graphic_lenx * zoom - 10, y0 + 10);

        for (int i = 0; i < FUNCTION_SIZE - 1; i ++)

            {

            txCircle ( x0 + x[i] * zoomx, y0 - y[i] * zoomy, 3);
            txCircle ( x0 + x[i + 1] * zoomx, y0 - y[i + 1] * zoomy, 3);
            txLine ( x0 + x[i] * zoomx, y0 - y[i] * zoomy, x0 + x[i + 1] * zoomx, y0 - y[i + 1] * zoomy);

            }

        for (int b = 0; b <= FUNCTION_SIZE; b = b + FUNCTION_SIZE/10)

            {

            txTextOut (x0 + x[b] * zoomx, y0 + 10, x[b]);
            txTextOut (x0 - 40, y0 - y[b] * zoomy, y[b]);

            }


        if (GetAsyncKeyState (VK_SPACE)) break;
        if (GetAsyncKeyState (87)) zoomy = zoomy * 1.01;
        if (GetAsyncKeyState (83)) zoomy = zoomy * 0.99;
        if (GetAsyncKeyState (68)) zoomx = zoomx * 1.01;
        if (GetAsyncKeyState (65)) zoomx = zoomx * 0.99;
        if (GetAsyncKeyState (VK_UP)) y0 = y0 - 7;
        if (GetAsyncKeyState (VK_DOWN))y0 = y0 + 7;
        if (GetAsyncKeyState (VK_RIGHT))x0 = x0 + 7;
        if (GetAsyncKeyState (VK_LEFT)) x0 = x0 - 7;
        txSetColor (TX_BLACK, 2);
        txSetFillColor (TX_BLACK);
        txSleep (200);
        txClear ();

        }

    }

