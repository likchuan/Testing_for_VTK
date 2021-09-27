## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/likchuan/Testing_for_VTK/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

# Mesh
<script type="text/javascript" src="https://unpkg.com/vtk.js"></script>
<div id="container" style="height: 500px; width: 500px; "></div>
<script type="text/javascript">

  const container = document.querySelector('#container');
  const dims = container.getBoundingClientRect();

  // VTK renderWindow/renderer
  const renderWindow = vtk.Rendering.Core.vtkRenderWindow.newInstance();
  const renderer     = vtk.Rendering.Core.vtkRenderer.newInstance();
  renderWindow.addRenderer(renderer);

  // WebGL/OpenGL impl
  const openGLRenderWindow = vtk.Rendering.OpenGL.vtkRenderWindow.newInstance();
  openGLRenderWindow.setContainer(container);
  openGLRenderWindow.setSize(dims.width, dims.height);
  renderWindow.addView(openGLRenderWindow);

  // Interactor
  const interactor = vtk.Rendering.Core.vtkRenderWindowInteractor.newInstance();
  interactor.setView(openGLRenderWindow);
  interactor.initialize();
  interactor.bindEvents(container);

  // Interactor style
  const trackball = vtk.Interaction.Style.vtkInteractorStyleTrackballCamera.newInstance();
  interactor.setInteractorStyle(trackball);

  // Pipeline
  const cone   = vtk.Filters.Sources.vtkConeSource.newInstance();
  const actor  = vtk.Rendering.Core.vtkActor.newInstance();
  const mapper = vtk.Rendering.Core.vtkMapper.newInstance();

  actor.setMapper(mapper);
  mapper.setInputConnection(cone.getOutputPort());
  renderer.addActor(actor);

  // Render
  renderer.resetCamera();
  renderWindow.render();

</script>


Check out [vtk](https://likchuan.github.io/Testing_for_VTK/standalone.html)

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/likchuan/Testing_for_VTK/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
