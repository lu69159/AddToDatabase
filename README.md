# AddToDatabase

一个替代ACD前置模组修复星球建筑的JS脚本，提供了几个函数来添加星球内容。

使用方法：在你的模组的scripts文件夹下放置ATD.js文件，然后在你的星球JS脚本中添加: const ATD = require("ATD");

  
添加后即可使用以下函数：

  ATD.AddAllToDatabase(modname, myplanet); //此函数能自动将属于你模组的所有内容添加到myplanet星球
  
  ATD.AddPlanetToDatabase(planet, myplanet); //此函数能将已有星球的所有内容添加到myplanet星球
  
  ATD.AddPlanetToDatabaseWithoutSectors(planet, myplanet); //此函数能将已有星球的所有内容添加到myplanet星球(核心数据库不添加区块内容)
  
  ATD.AddPlanetToDatabaseWithFunc(planet, myplanet, func); //此函数能将已有星球的内容添加到myplanet星球，添加的条件取决于func
  
  
以下是几个添加示例：

  把赛普罗星球的所有内容添加到myplanet星球: ATD.AddPlanetToDatabase(Planets.serpulo, myplanet);
  
  把模组名为"模组"的MOD里所有内容添加到myplanet星球：ATD.AddAllToDatabase("模组", myplanet);
  
  把赛普罗星球的所有内容添加到myplanet星球，但是不添加发射台和接受台：
  
  ATD.AddPlanetToDatabaseWithFunc(Planets.serpulo, myplanet, (thing) => {thing != Blocks.advancedLaunchPad && thing != Blocks.landingPad }); 
  
  
这是作者的MOD中星球的示例，实现了在Nepture星球添加了模组内容和赛普罗星球中除【赛普罗地图区块，发射台，接受台，行星际加速器】外的所有内容：

  const NT = new Planet("Nepture", Planets.sun, 1.2, 2.5);
  
  ...... //星球设置相关代码
  
  exports.NT = NT;
  
  const ATD = require("base/ATD");
  
  ATD.AddAllToDatabase("液体工艺", NT);
  
  ATD.AddPlanetToDatabaseWithFunc(Planets.serpulo, NT, (thing) => {
  	return !(thing instanceof SectorPreset) && thing != Blocks.advancedLaunchPad &&
  		thing != Blocks.landingPad && thing != Blocks.interplanetaryAccelerator;
  });
  
  ATD.AddPlanetToDatabaseWithoutSectors(NT, Planets.serpulo);
  

有任何问题可以联系作者，QQ:2909165527

# AddToDatabase

A JS script that replaces the ACD prerequisite mod to fix planet buildings. It provides several functions to add planet content.

Usage: Place the ATD.js file in the scripts folder of your mod, then add the following to your planet JS script: const ATD = require("ATD");

  
After adding, you can use the following functions:

  ATD.addAllToDatabase(modname, myplanet);// This function automatically adds all content belonging to your mod to the myplanetplanet.
  
  ATD.AddPlanetToDatabase(planet, myplanet);// This function adds all content from an existing planet to the myplanetplanet.
  
  ATD.AddPlanetToDatabaseWithoutSectors(planet, myplanet);// This function adds all content from an existing planet to the myplanetplanet (without adding sector content to the core database).
  
  ATD.AddPlanetToDatabaseWithFunc(planet, myplanet, func);// This function adds content from an existing planet to the myplanetplanet, with the condition of addition determined by func.
  
  
Here are some addition examples:

  Add all content from the Serpulo planet to myplanet: ATD.AddPlanetToDatabase(Planets.serpulo, myplanet);
  
  Add all content from a mod named "模组" to myplanet: ATD.AddAllToDatabase("模组", myplanet);
  
  Add all content from the Serpulo planet to myplanet, but exclude launch pads and landing pads:
  
  ATD.AddPlanetToDatabaseWithFunc(Planets.serpulo, myplanet, (thing) => {thing != Blocks.advancedLaunchPad && thing != Blocks.landingPad });
  

Below is an example from the author's mod planet, which adds mod content to the Neptune planet, as well as all content from Serpulo except 【Serpulo map sectors, launch pads, landing pads, and the interplanetary accelerator】:

  const NT = new Planet("Nepture", Planets.sun, 1.2, 2.5);
  
  ...... //planet setup code
  
  exports.NT = NT;
  
  const ATD = require("base/ATD");
  
  ATD.AddAllToDatabase("液体工艺", NT);
  
  ATD.AddPlanetToDatabaseWithFunc(Planets.serpulo, NT, (thing) => {
  	return !(thing instanceof SectorPreset) && thing != Blocks.advancedLaunchPad &&
  		thing != Blocks.landingPad && thing != Blocks.interplanetaryAccelerator;
  });
  
  ATD.AddPlanetToDatabaseWithoutSectors(NT, Planets.serpulo);
  

If you have any questions, you can contact the author，QQ:2909165527

