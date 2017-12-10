# Furier-Fingerprints-Graphic
#include "txlib.h"

void placedot ( float x, float y, int zoomy, int zoomx);
void graphic ( float x[], float y[]);


void graphic ( float x[], float y[])

    {

    txCreateWindow ( 1100, 650);
    txSetColor (TX_WHITE, 2);
    txSetFillColor (TX_WHITE);
    txLine ( 50, 25, 50, 625);
    txLine ( 50, 625, 1050, 625);
    float biggesty = y[0];
    for (int i = 1; i < FUNCTION_SIZE; i++)

        {

        if (biggesty < y[i]) biggesty = y[i];

        }

    int zoomy = 580/biggesty;
    int zoomx = 950/x[FUNCTION_SIZE - 1];
    for (int i = 0; i < FUNCTION_SIZE - 1; i ++)

        {

        placedot ( x[i], y[i], zoomy, zoomx);
        placedot ( x[i + 1], y[i + 1], zoomy, zoomx);
        txLine (x[i + 1] * zoomx, 625 - (y[i + 1] * zoomy), x[i] * zoomx, 625 - (y[i] * zoomy));

        }


    }

void placedot (float x, float y, int zoomy, int zoomx)

    {

    txCircle ( x * zoomx,625 - (y * zoomy), 4);

    }
