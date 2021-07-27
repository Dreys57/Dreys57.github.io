# Demo Scene GPR5300

## Context

This post is about a 3D scene I had to make for my GPR5300 class at SAE Institute Geneva. I used OpenGL for this scene, as well as C++. The tutorial LearnOpenGL has been a great
help throughout this project.

## Skybox

The first thing I did was make a skybox using a cubemap.

To do this, I made an array of vertices to place my skybox before loading and adding the textures.

![image](https://user-images.githubusercontent.com/55787228/127182012-7ffdd4a3-4808-4920-aa3f-bd0e181ff878.png)

As you can see, there are different faces for the skybox. The only problem when creating a skybox is making sure you load the faces in the right order, because if you don't,
you might end up with faces in the wrong place and the illusion of the skybox is broken.

## Plane and Tree

Secondly, I decided to do a simple flat plane. For that, as for the skybox, I had to create the vertices for it. 
From that, I loaded the texture for it, applying it to the whole plane and rendered it on the scene.

<img width="868" alt="plane" src="https://user-images.githubusercontent.com/55787228/127192122-42941fff-5aa3-41f0-a137-e80ca2383c3b.PNG">

The tree, unlike the plane, was a .obj model. For that, I had to load the obj and find and load the materials and textures for it before rendering it in the scene.

<img width="869" alt="treeAndPlane" src="https://user-images.githubusercontent.com/55787228/127192136-8a6b56cf-48e1-4344-b225-ef4fddbe4d5f.PNG">

And when both of these are rendered, the program renders the skybox behind.

<img width="872" alt="treeAndPlaneAndSkybox" src="https://user-images.githubusercontent.com/55787228/127193197-545f0c61-136e-4805-a955-de3c837a04b8.PNG">

## Shadow Mapping

Another technique I used was Shadow Mapping. Shadow Mapping is the technique to create shadows of objects when illuminated.

![image](https://user-images.githubusercontent.com/55787228/127193750-720cd77f-7607-40c1-a295-fa31df2e268e.png)

The idea is to have a light (in my project, I used a directional light) and, from the point of view of the light we draw the scene. We get the depth map that will be useful
to place shadows.

<img width="280" alt="shadowMap" src="https://user-images.githubusercontent.com/55787228/127194563-ae0b5632-43f5-478b-bba7-8c247b65920c.PNG">

With this depth map, we can do another rendering pass to render the objects and calculate the light and shadows.

![treeAndPlaneAndSkybox_LI](https://user-images.githubusercontent.com/55787228/127195168-5445106a-457a-47cb-a03b-5e108d7555a2.jpg)

![image](https://user-images.githubusercontent.com/55787228/127195207-e0cb5ee2-b706-48db-aacc-64df4b4e9e0c.png)

The thing that can happen when using Shadow Mapping is called Shadow acne:

![image](https://user-images.githubusercontent.com/55787228/127195373-2a85eee9-fe98-485a-a509-a43d22e63af2.png)

What happens is that sometimes, multiple fragments can sample from the same value from the depth map, creating these lines.To remedy that, in the shader, we use a bias to offset
the depth map to avoid this.

![image](https://user-images.githubusercontent.com/55787228/127195940-0d5dd5e5-d45f-4564-acd7-c1521f56a52f.png)

## Conclusion

Learning about graphics was really interesting and way more complicated than it seems on the surface. I would have loved to do more on my project, but due to personal reasons,
I was short on time. But I'll certainly keep learning about graphics and OpenGL in the future.

![DemoScene](https://user-images.githubusercontent.com/55787228/127197879-25b6a550-e081-4be5-b7f7-a77149a1b18d.gif)
