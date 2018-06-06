# Tool integration with Boutiques

To facilitate tool integration in CBRAIN, it is possible to use a [Boutiques](https://boutiques.github.io/) descriptor. Boutiques is a JSON specification that allows the command-line parameters of scientific tools to be described in a portable and standard manner, it includes the expected input files, parameter names, and the output result files that tool generates.
 
The Boutiques descriptor is used by CBRAIN in order to automatically generate web pages and Ruby code for tools, based on the parameter description. This should allowed faster tool integration since it did not require programmation knowledge.

In addition, to avoid frequent installation of tools on many distributed servers, CBRAIN can use a Singularity image containing the tool. The Singularity container can be retrieved from SingularityHub or register locally in CBRAIN. 

## 1. Create a Boutiques descriptor. 

Boutiques already have a solid documentation about how to write a Boutiques descriptor [here](https://github.com/boutiques/boutiques/blob/master/examples/Getting%20Started%20with%20Boutiques.ipynb)

You can also go further [launch your tool locally](https://github.com/boutiques/boutiques#launch-your-tool) and [test](https://github.com/boutiques/boutiques#test-your-tool) your tool.

## 2. Integrate your tool in CBRAIN 

**Important note**: if in your Boutiques descriptor the container image type is set to `singularity` you should have Singularity present on your Bourreau to be able to configure the tool. 
To setup Singularity on the Bourreau side, you need to go to the Bourreau show page and set in the `Container Configuration` session the `Singularity executable` value.

To integrate your tool in CBRAIN you need: 
1. To put your Boutiques descriptor under `BrainPortal/cbrain_plugins/cbrain-plugins-*/cbrain_task_descriptors` with `*` being an arbitraty name. You can have multiple descriptors (for multiple tool) in this directory.
2. On the BrainPortal side, under `BrainPortal` run the following: 
  > rake cbrain:plugins:install:all
3. On the Bourreau side, under `Bourreau` run the following: 
  > rake cbrain:plugins:install:plugins
4. After that restart your BrainPortal and your Bourreau. 

At this point, your tool should appear on the tool index page, and a tool configuration should be available on the Bourreau.  


