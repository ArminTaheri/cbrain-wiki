# Tool integration with Boutiques

To facilitate tool integration in CBRAIN, it is possible to use a [Boutiques](https://boutiques.github.io/) descriptor. Boutiques is a JSON specification that allows the command-line parameters of scientific tools to be described in a portable and standard manner. It includes the expected input files, parameter names, and the output result files that tool generates.
 
The Boutiques descriptor is used by CBRAIN in order to automatically generate web pages and Ruby code for tools based on the parameter description. This allows faster tool integration since it does not require additional programming.

In addition, to avoid frequent installation of tools on many distributed servers, CBRAIN can use a Singularity image containing the tool. The Singularity container can be retrieved from SingularityHub or be registered locally in CBRAIN. 

## 1. Create a Boutiques descriptor. 

Boutiques already has solid documentation on how to write a Boutiques descriptor [here](https://github.com/boutiques/boutiques/blob/master/examples/Getting%20Started%20with%20Boutiques.ipynb)

You can also [launch your tool locally](https://github.com/boutiques/boutiques#launch-your-tool) and [test](https://github.com/boutiques/boutiques#test-your-tool) your tool.

## 2. Integrate your tool in CBRAIN

**Important note**: if in your Boutiques descriptor the container image type is set to `singularity` you should have Singularity present on your Bourreau to be able to configure the tool. 
To setup Singularity on the Bourreau you need to go to the Bourreau show page and set in the `Container Configuration` session the `Singularity executable` value.

To integrate your tool in CBRAIN you need: 
1. To put your Boutiques descriptor under `BrainPortal/cbrain_plugins/cbrain-plugins-*/cbrain_task_descriptors` with `*` being an arbitrary name. You can have multiple descriptors (for multiple tools) in this directory.
2. On the BrainPortal side, in the `BrainPortal` folder, run the following: 
  > rake cbrain:plugins:install:all
3. On the Bourreau side, in the `Bourreau` folder, run the following: 
  > rake cbrain:plugins:install:plugins
4. After that restart your BrainPortal and your Bourreau. 

At this point, your tool should appear on the tool index page, and a tool configuration should be available on the Bourreau.

