# beet2mpd

A bridge between beets and mpd. Lets you add songs to mpd using the
advanced query syntax system of beets.

# SYNOPSIS

    beet2mpd
    beet2mpd comp:1
    beet2mpd loved:1
    beet2mpd genre:game
    beet2mpd mbid_trackid::^$
    beet2mpd label:'Masters of Hardcore'
    beet2mpd year:2000..2004 ^genre:pop,rock,rap,hip-hop
    beet2mpd comments:foo # do note the plural form!

# ENVIRONMENT

**${XDG\_MUSIC\_DIR}** should be set to the same directory as your library in
_beets/config.yaml_

Keep in mind that beets and mpd should be in sync, or else:

    {add} No such directory at /home/scp1/lib/perl5/Audio/MPD.pm line 156

Though accounted for in the error handling, this will mean that some
results from a given query won't be added to the playlist.

# INSTALLATION

## cpanminus

    $ cd beet2mpd/
    $ cpanm .

## Manual method

    $ cd beet2mpd/
    $ cpan Audio::MPD Term::ExtendedColor File::LsColor Try::Tiny
    $ perl Makefile.PL
    $ make
    # make install

# AUTHOR

    Magnus Woldrich
    CPAN ID: WOLDRICH
    m@japh.se
    japh@irc.libera.chat
    http://japh.se
    http://github.com/trapd00r

# COPYRIGHT

Copyright 2021 Magnus Woldrich
