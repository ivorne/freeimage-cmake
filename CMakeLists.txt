cmake_minimum_required( VERSION 3.10 )

#-------- project ---------------------------------------------------
project( FreeImage )

set( CMAKE_C_STANDARD 90 )
set( CMAKE_CXX_STANDARD 11 )

#-------- sources ---------------------------------------------------
set( cpp_INCLUDES freeimage/Source freeimage/Source/Metadata freeimage/Source/FreeImageToolkit freeimage/Source/ZLib )
set( cpp_SOURCES freeimage/Source/FreeImage/BitmapAccess.cpp freeimage/Source/FreeImage/ColorLookup.cpp freeimage/Source/FreeImage/FreeImage.cpp freeimage/Source/FreeImage/FreeImageC.c freeimage/Source/FreeImage/FreeImageIO.cpp freeimage/Source/FreeImage/GetType.cpp freeimage/Source/FreeImage/MemoryIO.cpp freeimage/Source/FreeImage/PixelAccess.cpp freeimage/Source/FreeImage/J2KHelper.cpp freeimage/Source/FreeImage/MNGHelper.cpp freeimage/Source/FreeImage/Plugin.cpp freeimage/Source/FreeImage/PSDParser.cpp freeimage/Source/FreeImage/TIFFLogLuv.cpp freeimage/Source/FreeImage/Conversion.cpp freeimage/Source/FreeImage/Conversion16_555.cpp freeimage/Source/FreeImage/Conversion16_565.cpp freeimage/Source/FreeImage/Conversion24.cpp freeimage/Source/FreeImage/Conversion32.cpp freeimage/Source/FreeImage/Conversion4.cpp freeimage/Source/FreeImage/Conversion8.cpp freeimage/Source/FreeImage/ConversionFloat.cpp freeimage/Source/FreeImage/ConversionRGB16.cpp freeimage/Source/FreeImage/ConversionRGBA16.cpp freeimage/Source/FreeImage/ConversionRGBAF.cpp freeimage/Source/FreeImage/ConversionRGBF.cpp freeimage/Source/FreeImage/ConversionType.cpp freeimage/Source/FreeImage/ConversionUINT16.cpp freeimage/Source/FreeImage/Halftoning.cpp freeimage/Source/FreeImage/tmoColorConvert.cpp freeimage/Source/FreeImage/tmoDrago03.cpp freeimage/Source/FreeImage/tmoFattal02.cpp freeimage/Source/FreeImage/tmoReinhard05.cpp freeimage/Source/FreeImage/ToneMapping.cpp freeimage/Source/FreeImage/LFPQuantizer.cpp freeimage/Source/FreeImage/NNQuantizer.cpp freeimage/Source/FreeImage/WuQuantizer.cpp freeimage/Source/FreeImage/CacheFile.cpp freeimage/Source/FreeImage/MultiPage.cpp freeimage/Source/FreeImage/ZLibInterface.cpp )
set( cpp_SOURCES ${cpp_SOURCES} freeimage/Source/DeprecationManager/Deprecated.cpp freeimage/Source/DeprecationManager/DeprecationMgr.cpp )
set( cpp_SOURCES ${cpp_SOURCES} freeimage/Source/Metadata/Exif.cpp freeimage/Source/Metadata/FIRational.cpp freeimage/Source/Metadata/FreeImageTag.cpp freeimage/Source/Metadata/IPTC.cpp freeimage/Source/Metadata/TagConversion.cpp freeimage/Source/Metadata/TagLib.cpp freeimage/Source/Metadata/XTIFF.cpp )
set( cpp_SOURCES ${cpp_SOURCES} freeimage/Source/FreeImageToolkit/Background.cpp freeimage/Source/FreeImageToolkit/BSplineRotate.cpp freeimage/Source/FreeImageToolkit/Channels.cpp freeimage/Source/FreeImageToolkit/ClassicRotate.cpp freeimage/Source/FreeImageToolkit/Colors.cpp freeimage/Source/FreeImageToolkit/CopyPaste.cpp freeimage/Source/FreeImageToolkit/Display.cpp freeimage/Source/FreeImageToolkit/Flip.cpp freeimage/Source/FreeImageToolkit/JPEGTransform.cpp freeimage/Source/FreeImageToolkit/MultigridPoissonSolver.cpp freeimage/Source/FreeImageToolkit/Rescale.cpp freeimage/Source/FreeImageToolkit/Resize.cpp )
set( cpp_SOURCES ${cpp_SOURCES} freeimage/Source/ZLib/adler32.c freeimage/Source/ZLib/compress.c freeimage/Source/ZLib/crc32.c freeimage/Source/ZLib/deflate.c freeimage/Source/ZLib/gzclose.c freeimage/Source/ZLib/gzlib.c freeimage/Source/ZLib/gzread.c freeimage/Source/ZLib/gzwrite.c freeimage/Source/ZLib/infback.c freeimage/Source/ZLib/inffast.c freeimage/Source/ZLib/inflate.c freeimage/Source/ZLib/inftrees.c freeimage/Source/ZLib/trees.c freeimage/Source/ZLib/uncompr.c freeimage/Source/ZLib/zutil.c )

include( "Options.cmake" )

if( IV_FREEIMAGE_PNG )
	
	set( cpp_INCLUDES ${cpp_INCLUDES} freeimage/Source/LibPNG )
	set( cpp_SOURCES ${cpp_SOURCES} freeimage/Source/FreeImage/PluginPNG.cpp )
	set( cpp_SOURCES ${cpp_SOURCES} freeimage/Source/LibPNG/png.c freeimage/Source/LibPNG/pngerror.c freeimage/Source/LibPNG/pngget.c freeimage/Source/LibPNG/pngmem.c freeimage/Source/LibPNG/pngpread.c freeimage/Source/LibPNG/pngread.c freeimage/Source/LibPNG/pngrio.c freeimage/Source/LibPNG/pngrtran.c freeimage/Source/LibPNG/pngrutil.c freeimage/Source/LibPNG/pngset.c freeimage/Source/LibPNG/pngtrans.c freeimage/Source/LibPNG/pngwio.c freeimage/Source/LibPNG/pngwrite.c freeimage/Source/LibPNG/pngwtran.c freeimage/Source/LibPNG/pngwutil.c )
	
else()
	
	set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginPNG.cpp )
	
endif()

set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginBMP.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginICO.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginJPEG.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginJNG.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginKOALA.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginIFF.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginMNG.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginPNM.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginPCD.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginPCX.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginRAS.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginTARGA.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginTIFF.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginWBMP.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginPSD.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginCUT.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginXBM.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginXPM.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginDDS.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginGIF.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginHDR.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginG3.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginSGI.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginEXR.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginJ2K.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginJP2.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginPFM.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginPICT.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginRAW.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginWEBP.cpp )
set( cpp_SOURCES ${cpp_SOURCES} substitutions/PluginJXR.cpp )

#-------- binary ----------------------------------------------------
add_library( FreeImage ${cpp_SOURCES} )
target_include_directories( FreeImage INTERFACE freeimage/Source )
target_include_directories( FreeImage PRIVATE ${cpp_INCLUDES} )
target_compile_definitions( FreeImage PRIVATE -DNO_LCMS -D__ANSI__ -DDISABLE_PERF_MEASUREMENT )
target_compile_options( FreeImage PRIVATE -Wno-switch -Wno-bitwise-op-parentheses -Wno-logical-op-parentheses )

if( CMAKE_SYSTEM_NAME MATCHES "Android" )
	target_compile_definitions( FreeImage PRIVATE -DPNG_ARM_NEON_OPT=0 )
endif()
