project('boosttest', 'cpp')

if meson.get_compiler('cpp').get_id() != 'msvc'
  add_global_arguments('-std=c++11', language : 'cpp')
endif

# We want to have multiple separate configurations of Boost
# within one project. The need to be independent of each other.
# Use one without a library dependency and one with it.

nolinkdep = dependency('boost', modules: 'utility')
linkdep = dependency('boost', modules : ['thread', 'system'])

nolinkexe = executable('nolinkedexe', 'nolinkexe.cc', dependencies : nolinkdep)
linkexe = executable('linkedexe', 'linkexe.cc', dependencies : linkdep)

test('Boost nolinktext', nolinkexe)
test('Boost linktext', linkexe)
