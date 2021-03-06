# Alien::Libxml2 [![Build Status](https://secure.travis-ci.org/Perl5-Alien/Alien-Libxml2.png)](http://travis-ci.org/Perl5-Alien/Alien-Libxml2)

Install the C libxml2 library on your system

# SYNOPSIS

In your Build.PL:

    use Module::Build;
    use Alien::Libxml2;
    my $builder = Module::Build->new(
      ...
      configure_requires => {
        'Alien::Libxml2' => '0',
        ...
      },
      extra_compiler_flags => Alien::Libxml2->cflags,
      extra_linker_flags   => Alien::Libxml2->libs,
      ...
    );
    
    $build->create_build_script;

In your Makefile.PL:

    use ExtUtils::MakeMaker;
    use Config;
    use Alien::Libxml2;
    
    WriteMakefile(
      ...
      CONFIGURE_REQUIRES => {
        'Alien::Libxml2' => '0',
      },
      CCFLAGS => Alien::Libxml2->cflags . " $Config{ccflags}",
      LIBS    => [ Alien::Libxml2->libs ],
      ...
    );

In your [FFI::Platypus](https://metacpan.org/pod/FFI::Platypus) script or module:

    use FFI::Platypus;
    use Alien::Libxml2;
    
    my $ffi = FFI::Platypus->new(
      lib => [ Alien::Libxml2->dynamic_libs ],
    );

# DESCRIPTION

This module provides libxml2 for other modules to use.  There was an 
already existing [Alien::LibXML](https://metacpan.org/pod/Alien::LibXML), but it uses the older 
[Alien::Build::ModuleBuild](https://metacpan.org/pod/Alien::Build::ModuleBuild) and has not bee actively maintained for a 
while.

# SEE ALSO

- [Alien::LibXML](https://metacpan.org/pod/Alien::LibXML)

    Unmaintained Alien for the same library.

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2013 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
