# beet2mpd

A bridge between beets and mpd. Lets you add songs to mpd using the
advanced query syntax system of beets.

# SYNOPSIS

    beet2mpd                             # add everything
    beet2mpd comp:1                      # add compilations
    beet2mpd loved:1                     # https://github.com/trapd00r/utils/blob/master/love
    beet2mpd country:se                  # add music from sweden only
    beet2mpd genre:game                  # add game music
    beet2mpd mbid_trackid::^$            # add everything missing musicbrainz id
    beet2mpd label:'Masters of Hardcore' # add everything from a record label
    beet2mpd comments:foo                # do note the plural form!
    beet2mpd ^genre:rap albumtype:single # single releases that's NOT rap
    beet2mpd added:-1w..                 # add new music imported in the past week
    beet2mpd albumdisambig:explicit      # no censored lyrics

    # add official album releases
    beet2mpd albumtype:album albumstatus:official

    # add music released the day you were born
    beet2mpd original_day:14 original_month:8 original_year:1990

    # add music released this day in history
    beet2mpd original_day:$(date +%d) original_month:$(date +%m)

    # add music from year 2000-2004 that's NOT pop, rock, rap or hip-hop:
    beet2mpd year:2000..2004 \^genre:pop,rock,rap,hip-hop

    # add music from 1999 where album name contains love, but track
    # titles does not:
    beet2mpd  year:1999 album:love \^title:love

    # add new music imported in the past hour
    beet2mpd --hour 1 -v

    # make a query but don't add results to mpd; simply print the results
    # for possible piping to other applications.
    beet2mpd artist:lindfors --no-add --nocolor --hour 4 genre:pop

# OPTIONS

    All boolean options are enabled with --option and yet again
    disabled with --no-option. That is, you use the same option name but prefix
    it with 'no-'.

            --color  Enable or disable colorized output.
            --add,   Add or print results from a query.
            --hour   Add tracks added to beets n hour(s) ago.

      -v,   --verbose   Increase the verbosity. Can be specified multiple times.
      -h,   --help      Display this help and exit.

# ENVIRONMENT

**${XDG\_MUSIC\_DIR}** should be set to the same directory as your library in
_beets/config.yaml_

Keep in mind that beets and mpd should be in sync, or else:

    {add} No such directory at Audio/MPD.pm line 156

Though accounted for in the error handling, this will mean that some
results from a given query won't be added to the playlist.

# INSTALLATION

## cpanminus

    $ cd beet2mpd/
    $ cpanm .

## Manual method

    $ cd beet2mpd/
    $ cpan Audio::MPD File::LsColor Try::Tiny
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

Copyright 2021,2022 Magnus Woldrich
