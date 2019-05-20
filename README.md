### Houdini VEX  Snippets

Colección de "snippets" (trozos de código) para realizar funciones concretas. Se aplica a "wranglers" (nodos específicos de Houdini para albergar código VEX), o bien a otros nodos.

**Eliminar primer y ultimo punto de una primitiva (típicamente curvas)**
```C#
// Delete first and last curve points
//set a wrangle to run over primitives
int primpts[] = primpoints(0,@primnum);
removepoint(0,primpts[0]);
removepoint(0,primpts[-1]);
```

**Borrar puntos de forma aleatoria según una tolerancia** 

```C#
// This snippet will delete random points based on the threshold slider
// set a wrangle to run over points
if ( rand(@ptnum) > ch('threshold') ) {
   removepoint(0,@ptnum);
}
```
**Centrar el pivot y mover al origen de coordenadas** 

```C#
//  Center Pivot and Move to Origin
// set a wrangle to run over points
vector centroid = getbbox_center(0);
vector dist = centroid - 0;
v@P -= dist;
```