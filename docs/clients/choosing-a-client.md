Choosing a client {#sec:clients}
=================

Why are there multiple Ethereum clients?
----------------------------------------

From the earliest days of the project there have been multiple client
implementations across a range of different operating systems. That
client diversity is a huge win for the ecosystem as a whole. It lets us
verify that the protocol (specified in the [Yellow
Paper](https://github.com/ethereum/yellowpaper)) is unambiguous. It
keeps the door open for new innovation. It keeps us all honest. However,
it can be very confusing for end-users, because there is no universal
\"Ethereum Installer\" for them to use.

As of September 2016, the leading implementations are
[go-ethereum]{role="ref"} and [Parity]{role="ref"}.

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Client                          Language     Developers                                     Latest release
  ------------------------------- ------------ ---------------------------------------------- -------------------------------------------------------------------------------------------
  [go-ethereum]{role="ref"}       Go           [Ethereum                                      [go-ethereum-v1.4.18](https://github.com/ethereum/go-ethereum/releases/tag/v1.4.18)
                                               Foundation](https://ethereum.org/foundation)   

  [Parity]{role="ref"}            Rust         [Ethcore](https://ethcore.io/)                 [Parity-v1.4.0](https://github.com/ethcore/parity/releases/tag/v1.4.0)

  [cpp-ethereum]{role="ref"}      C++          [Ethereum                                      [cpp-ethereum-v1.3.0](https://github.com/bobsummerwill/cpp-ethereum/releases/tag/v1.3.0)
                                               Foundation](https://ethereum.org/foundation)   

  [pyethapp]{role="ref"}          Python       [Ethereum                                      [pyethapp-v1.5.0](https://github.com/ethereum/pyethapp/releases/tag/v1.5.0)
                                               Foundation](https://ethereum.org/foundation)   

  [ethereumjs-lib]{role="ref"}    Javascript   [Ethereum                                      [ethereumjs-lib-v3.0.0](https://github.com/ethereumjs/ethereumjs-lib/releases/tag/v3.0.0)
                                               Foundation](https://ethereum.org/foundation)   

  [Ethereum\\(J\\)]{role="ref"}   Java         [\\\<ether.camp\\\>](http://www.ether.camp)    [ethereumJ-v1.3.1](https://github.com/ethereum/ethereumj/releases/tag/1.3.1)

  [ruby-ethereum]{role="ref"}     Ruby         [Jan Xie](https://github.com/janx/)            [ruby-ethereum-v0.9.6](https://rubygems.org/gems/ruby-ethereum/versions/0.9.6)

  [ethereumH]{role="ref"}         Haskell      [BlockApps](http://www.blockapps.net/)         no Homestead release yet
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

What should I install on my desktop/laptop?
-------------------------------------------

Most users will likely just install [Mist / Ethereum
Wallet](https://github.com/ethereum/mist) and that will be enough for
their needs.

The Ethereum Wallet is a \"single dapp\" deployment of the **Mist
Browser** which will be the centerpiece of the Metropolis phase of
development, which comes after Homestead.

Mist comes with bundled [go-ethereum]{role="ref"} and
[cpp-ethereum]{role="ref"} binaries and if you are not running a
command-line Ethereum client when Mist starts then it will start syncing
the blockchain using one of the bundled clients (defaulting to
**geth**). If you want to use Parity with Mist, or to run Mist against a
private network, just start your node before Mist, and Mist will connect
to your node rather than starting one itself.

**Work is underway to add Parity and other clients as \"first-class
entities\" to Mist too.**

If you want to interact with Ethereum on the command-line, and to take
advantage of the Javascript console then you will want to install one of
the client applications directly, as well as Mist. Follow the links in
the table above for further instructions.

If you want to do mining then Mist will not be sufficient. Check out the
[mining]{role="ref"} section.

What should I install on my mobile/tablet?
------------------------------------------

We are at the very beginning of our support for mobile devices. The Go
team are publishing experimental iOS and Android libraries, which some
developers are using to start bootstrapping mobile applications, but
there are not yet any mobile Ethereum clients available.

The main hinderance to the use of Ethereum on mobile devices is that the
Light Client support is still incomplete. The work which has been done
is off in a private branch, and is only available for the Go client.
doublethinkco will be starting development of Light Client for the C++
client in the coming months, following grant funding.

Check out [Status.im](http://status.im), who were initially using
[ethereumj-personal](https://github.com/status-im/ethereumj-personal)
based on [Ethereum(J)]{role="ref"}, but have recently flipped to Geth
cross-builds with Light Client.

What should I install on my SBC?
--------------------------------

You have some choice here depending on your skill level, and what you
are looking to do.

-   Download a fully prepared image(link to page with detailed download
    & install instructions)
    -   If you are new to Ethereum AND SBC boards such as the Raspberry
        Pi then this is for you! Simply download the image specific to
        the dev board you are working with, burn it to an SD card, boot
        your device, and run Ethereum!
-   Download a pre-compiled application(link to page with detailed
    download & install instructions)
    -   If you already have an SBC running and have a specific,
        preferred OS or setup that you want to keep, then this is your
        best option! Depending on the platform, you can simply download
        the apropriate executable, and with minimal linking of libraries
        and setting of PATH you can have Ethereum running in your
        existing environment!
-   Build from source using customizable scripts(link to page with more
    detail and individual SBC links to <https://github.com/ethembedded>)
    -   Looking to perform a custom install? We have scripts available
        to compile from source \"on device\". Our scripts contain
        auto-install of dependencies as well as the client itself. This
        will allow you to install a specific version of the Ethereum
        client(i.e.-\"develop\", \"master\", etc.), compile your own
        forked version of a client, and generally play around with the
        intracacies of the build process.

Interacting with Clients
========================

In order to interact with Ethereum clients programatically, please refer
to the [Connecting to Clients]{role="ref"} section.
