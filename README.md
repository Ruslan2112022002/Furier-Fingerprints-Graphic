# Furier-Fingerprints-Graphic
#include "txlib.h"

void graphiks (float x[], float y[], const int posTstart, const int posTend, float antiT, const int start, const int end);
void placedot (float x, float y, int zoomx, int zoomy);

void graphiks (float x[], float y[], const int posTstart, const int posTend, float antiT, const int start, const int end)

    {

    txCreateWindow (1400,1000);
    txSetFillColor (TX_WHITE);
    txSetColor (TX_WHITE, 2);
    txLine ( 100, 50, 100, 900);
    txLine ( 100, 900, 1350, 900);
    y[0] = dumbIn(posTstart, posTend+1, start, end)*antiT/2;
    float biggesty = y[0];
    for (int i = 1; i < FUNCTION_SIZE; i ++)

        {

        if (biggesty <= x[i]) biggesty = y[i];

        }

    int zoomy = 800/biggesty;
    int zoomx = 1200/x[FUNCTION_SIZE - 1];

    for (int i = 0; i < FUNCTION_SIZE - 1; i ++)

        {

        placedot ( x[i], y[i], zoomx, zoomy);
        placedot ( x[i + 1], y[i + 1], zoomx, zoomy);
        txLine (x[i] * zoomx, y[i] * zoomy,  x[i + 1] * zoomx, y[i + 1] * zoomy);

        }



    }

void placedot (float x, float y, int zoomx, int zoomy)

    {

    txCircle ( x * zoomx, y * zoomy, 10);
    txCircle (x * zoomx, y*zoomy , 4);

    }
