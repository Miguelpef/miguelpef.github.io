---
layout: post
title: UE4 Opciones Gráficas Android
author: MiguelPeF
Categories: Rashan Project, Opciones gráficas, gráficos
---

![_config.yml]({{ site.baseurl }}/images/graficos/Graficos.png)

Dentro del mundo Android encontramos muchas diferencias entre dispositivos. A nivel de Hardware es un gran impedimento para la reproducción de aplicaciones que requieran una gran potencia. 
En este sentido el juego que estoy desarrollando necesita de las mejores condiciones para funcionar ya que se desarrolla bajo OpenGL ES 3.1 un render específico para móvil con un componente visual muy potente. Para más información sobre OpenGL ES 3.1 puedes ir a este <a href="https://docs.unrealengine.com/en-US/Platforms/Mobile/Android/OpenGLES31MobileRenderer/index.html">enlace</a>.

<h2>Gestionando la configuración gráfica en Android</h2>
En primer lugar hay que dar la posibilidad de cambiar las opciones gráficas desde algún tipo de menú que se encuentre tanto en el inicio del juego por si el dispositivo no puede iniciarlo con la máxima calidad posible y otro durante el juego por si en cualquier momento se quiere cambiar por cualquier motivo.
Para ello usaremos tres botones, calidad alta, calidad media y calidad baja. Lo único que cambiaremos por el momento será el porcentaje de resolución de pantalla, haciendo que en la calidad más baja se llegue a distorsionar la imagen y dando a los bordes unos dientes de sierra que si bien empeoran la experiencia de juego, permiten aceptar un mayor número de dispositivos.
</br>
Para realizar este cambio ejecutaremos en consola los siguientes comandos:
- r.ScreenPercentage 40
- r.ScreenPercentage 80
- r.ScreenPercentage 100

Donde el número es el porcentaje de resolución que comprende desde el 0 hasta el 100 siendo este último la máxima posible. Puedes ver más información sobre esta opción en el siguiente <a href="https://docs.unrealengine.com/en-US/Resources/ContentExamples/PostProcessing/1_13/index.html">enlace</a>.
![_config.yml]({{ site.baseurl }}/images/graficos/settinggraph.png)
</br>
<h2>Ejemplo y diferencias entre las distintas resoluciones en dispositivo Android</h2>
<h3>Calidad Baja</h3>
![_config.yml]({{ site.baseurl }}/images/graficos/Lowset.png)
</br>
<h3>Calidad Media</h3>
![_config.yml]({{ site.baseurl }}/images/graficos/mediumset.png)
</br>
<h3>Calidad Alta</h3>
![_config.yml]({{ site.baseurl }}/images/graficos/highset.png)
</br>
<h2>Otros comandos para cambiar la configuración gráfica</h2>
El número que se escribe es el rango entre el que se puede variar la configuración, si nos encontramos 0-4 podemos poner 0,1,2,3,4 pero solo un número que será la configuración que tendrá.
<b>Post Procesado</b>
<code>
r.MotionBlurQuality=0-4</br>
r.BlurGBuffer=0-1</br>
r.AmbientOcclusionLevels=0-3</br>
r.AmbientOcclusionRadiusScale=1.7-1.0</br>
r.DepthOfFieldQuality=0-2</br>
r.RenderTargetPoolMin=300-400</br>
r.LensFlareQuality=0-2</br>
r.SceneColorFringeQuality=0-1</br>
r.EyeAdaptationQuality=0-2</br>
r.BloomQuality=4-5</br>
r.FastBlurThreshold=0-7</br>
r.Upscale.Quality=1-3</br>
r.Tonemapper.GrainQuantization=0-1</br>
</code>
</br>
<b>Sombras</b>
<code>
r.LightFunctionQuality=0-1</br>
r.ShadowQuality=0-5</br>
r.Shadow.CSM.MaxCascades=1-4</br>
r.Shadow.MaxResolution=512-1024</br>
r.Shadow.RadiusThreshold=0.06-0.03</br>
r.Shadow.DistanceScale=0.6-1.0</br>
r.Shadow.CSM.TransitionScale=0-1.0</br>
</code>
</br>
<b>Texturas</b>
<code>
r.Streaming.MipBias=2.5-0</br>
r.MaxAnisotropy=0-8</br>
r.Streaming.PoolSize=200-1000</br>
</code>
</br>
<b>Efectos</b>
<code>
r.TranslucencyLightingVolumeDim=24-64</br>
r.RefractionQuality=0-2</br>
r.SSR=0-1</br>
r.SceneColorFormat=3-4</br>
r.DetailMode=0-2</br>
r.TranslucencyVolumeBlur=0-1</br>
r.MaterialQualityLevel=0-1</br>
</code>
</br>
</br>
</br>
Para más información acerca de las opciones gráficas en Unreal Engine 4 ir al siguiente <a href="https://docs.unrealengine.com/en-US/Engine/Performance/Scalability/ScalabilityReference/index.html">enlace</a>.
