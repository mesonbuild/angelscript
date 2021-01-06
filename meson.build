project('angelscript', 'cpp',
        version : run_command(find_program('python3'), 'angelscript/projects/meson/detect_ver.py').stdout().strip(),
        meson_version : '>=0.28.0',
        license : 'zlib')

threads = dependency('threads')

angel_srcs = files(
  'angelscript/source/as_atomic.cpp',
  'angelscript/source/as_builder.cpp',
  'angelscript/source/as_bytecode.cpp',
  'angelscript/source/as_callfunc.cpp',
  'angelscript/source/as_callfunc_mips.cpp',
  'angelscript/source/as_callfunc_ppc.cpp',
  'angelscript/source/as_callfunc_ppc_64.cpp',
  'angelscript/source/as_callfunc_sh4.cpp',
  'angelscript/source/as_callfunc_x86.cpp',
  'angelscript/source/as_callfunc_x64_gcc.cpp',
  'angelscript/source/as_callfunc_x64_mingw.cpp',
  'angelscript/source/as_compiler.cpp',
  'angelscript/source/as_context.cpp',
  'angelscript/source/as_configgroup.cpp',
  'angelscript/source/as_datatype.cpp',
  'angelscript/source/as_generic.cpp',
  'angelscript/source/as_gc.cpp',
  'angelscript/source/as_globalproperty.cpp',
  'angelscript/source/as_memory.cpp',
  'angelscript/source/as_module.cpp',
  'angelscript/source/as_objecttype.cpp',
  'angelscript/source/as_outputbuffer.cpp',
  'angelscript/source/as_parser.cpp',
  'angelscript/source/as_restore.cpp',
  'angelscript/source/as_scriptcode.cpp',
  'angelscript/source/as_scriptengine.cpp',
  'angelscript/source/as_scriptfunction.cpp',
  'angelscript/source/as_scriptnode.cpp',
  'angelscript/source/as_scriptobject.cpp',
  'angelscript/source/as_string.cpp',
  'angelscript/source/as_string_util.cpp',
  'angelscript/source/as_thread.cpp',
  'angelscript/source/as_tokenizer.cpp',
  'angelscript/source/as_typeinfo.cpp',
  'angelscript/source/as_variablescope.cpp',
)
if host_machine.cpu_family() == 'arm'
  add_languages('c')
  angel_srcs += files(
    'angelscript/source/as_callfunc_arm.cpp',
    'angelscript/source/as_callfunc_arm_gcc.S',
  )
endif

angelscript_version_num = run_command(find_program('python3'), 'angelscript/projects/meson/detect_ver.py', '--num').stdout().strip()
angelscript_lib = library(
  'angelscript',
  sources : angel_srcs,
  dependencies : threads,
  version : angelscript_version_num,
  install : true,
)
angelscript_inc = include_directories('angelscript/include')
angelscript_dep  = declare_dependency(
  link_with : angelscript_lib,
  include_directories : angelscript_inc,
  version : meson.project_version(),
)

install_headers('angelscript/include/angelscript.h')
