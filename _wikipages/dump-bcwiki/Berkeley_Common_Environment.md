---
title: Berkeley Common Environment
permalink: /Berkeley_Common_Environment/
---

EE123 in the BCE
----------------

### Caveats

Big old caveat: obviously I've never taken this course, so I can't tell you ahead of time whether some additional configuration will be necessary to get the hardware used in the labs to play nice with the BCE VM. What I CAN tell you is that I'll figure this out as we go along and post my findings here. I'll do what I can, but don't expect configuration help from the TAs if you have a problem.

This option has many advantages but it'll cost you some diskspace—I'd recommend having at least 20GB free.

### Rationale

Another option for managing the software you'll need in this course is to use the Berkeley Common Environment (BCE), an Ubuntu Linux virtual machine (VM) that has been customized by the Berkeley IT department for STEM classwork, learning, and research. This is nice because it works in any host operating system and it's completely self-contained—it won't interfere with any of your software or settings and it will look and work identically regardless of your host OS. Installing the software required for this course on this VM can be much easier and less error-prone than installing it on your host OS.

Another benefit is that you'll have a complete, independent Unix environment to play and learn in, right inside the comfort of your host OS! And that's just awesome.

### Installing the BCE

To use the BCE VM, install a virtual machine manager such as the open source VirtualBox: <https://www.virtualbox.org/>

Next, download the BCE virtual appliance in [.ova format](http://en.wikipedia.org/wiki/Open_Virtualization_Format): <http://bce.berkeley.edu/>. This is a large file (3.6GB).

Run VirtualBox, hit File → Import Appliance, select the .ova file you downloaded, and that's that! Fire up the VM and configure it for EE123.

If the VM refuses to run, see the BCE troubleshooting tips: <http://bce.berkeley.edu/troubleshooting-tips.html>. Most commonly, you'll need to turn on the virtualization feature in your BIOS.

### Configuring the BCE for EE123

You can install software on the VM just like you would on your host operating system.

First, launch a terminal by clicking on the icon or with `ctrl-alt-t` and make sure the BCE is up to date:

`sudo` `apt-get` `--yes` `--force-yes` `update` `&&` `sudo` `apt-get` `--yes` `--force-yes` `upgrade` `&&` `sudo` `apt-get` `--yes` `--force-yes` `dist-upgrade` `&&` `sudo` `apt-get` `--yes` `--force-yes` `autoremove`

Now install iPython, RTL-SDR software (part of gnuradio), and PyAudio. This will automatically install [Matplotlib](http://en.wikipedia.org/wiki/Matplotlib), [NumPy](http://en.wikipedia.org/wiki/NumPy), and [SciPy](http://en.wikipedia.org/wiki/SciPy), but I list them here anyway for completeness:

`sudo` `apt-get` `install` `ipython` `gnuradio` `python-pyaudio` `python-matplotlib` `python-scipy` `python-numpy`

There are thousands of Python packages available, and many aren't present in the Ubuntu software repositories. Fortunately, the [Python Packaging Authority](https://www.pypa.io/) maintains a brilliant tool called [PIP](https://pip.pypa.io/en/latest/) ("Python Install Python") for easily managing and maintaining Python packages. PIP now comes with Python 2.7.9+, so no need to install it.

You can use PIP to install the last requirement, [Bokeh](http://bokeh.pydata.org/en/latest/): `sudo` `pip` `install` `bokeh`

You should now be good to go! Launch iPython with `ipython` `notebook`

### Getting Fancy with Virtual Environments

**This section is not necessary**—it's an alternative for advanced users, included FYI.

Sometimes you don't want to install a bunch of packages into the global, system-wide Python installation. Especially if you do development work and sometimes need to work with old packages that have strange dependencies, you could run the risk of running into incompatibilities or screwing up your system-wide Python and breaking everything that uses it. Fortunately, you can use virtual environments to create an independent box for each project and all of its dependencies, without changing the system-wide install (much like you're doing with this BCE VM!).

The easiest way to go about this is currently with `virtualenvwrapper`, which can be installed with PIP:

`sudo` `pip` `install` `virtualenvwrapper`

Set up `virtualenvwrapper` by creating a folder to save your project working directories:

`mkdir` `-p` `$HOME/Dev`

and adding this to the end of your shell startup file with `nano` `~/.bashrc` (you can paste in the nano text editor with ctrl-shift-v; save and exit with ctrl-X):

<code>

    export WORKON_HOME=$HOME/.virtualenvs
    export WORKON_HOME=$HOME/Dev
    source /usr/local/bin/virtualenvwrapper.sh

</code>

Now, reload your startup file:

`source` `~/.bashrc`

You can then create a new virtual environment—a new box to work in—with the `mkvirtualenv` <environment-name>:

<code>

    mkvirtualenv ee123
    mkvirtualenv temp

</code>

See existing environments and switch between them with `workon`. This command has tab completion, so type `workon`, followed by a space, and then tap <tab> twice to see all existing environments.

Once you've switched into an environment with `workon` <environment-name>, you can use pip to install packages into this environment (this isn't the system-wide install, so `sudo` isn't necessary):

<code>

    pip install ipython
    pip install numpy
    pip install scipy
    pip install matplotlib
    pip install bokeh
    pip install pyaudio

</code>

Installing `pyaudio` [throws errors](http://stackoverflow.com/questions/9634478/unable-to-install-pyaudio-on-osx-lion/10290595#10290595)!

Have to install a missing dependency first:

`sudo` `apt-get` `install` `portaudio19-dev`

PyAudio is somehow hosted externally and must be installed with:

`pip` `install` `--allow-unverified` `pyaudio` `--allow-all-external` `pyaudio`

See what packages are installed in the current environment with `pip` `freeze`.

Leave the virtual environment and return to the global Python install with `deactivate`.

Testing and Troubleshooting
---------------------------

### Verifying Audio

Inside the VM, download this example .WAV file:

`wget` [`https://ccrma.stanford.edu/~jos/wav/gtr-nylon22.wav`](https://ccrma.stanford.edu/~jos/wav/gtr-nylon22.wav)

Now fire up iPython and run this in a fresh notebook:

<code>

    """PyAudio Example: Play a WAVE file."""

    import wave
    import pyaudio

    CHUNK = 1024

    wf = wave.open('gtr-nylon22.wav', 'rb')

    p = pyaudio.PyAudio()

    stream = p.open(format=p.get_format_from_width(wf.getsampwidth()),
                    channels=wf.getnchannels(),
                    rate=wf.getframerate(),
                    output=True)

    data = wf.readframes(CHUNK)

    while data != '':
        stream.write(data)
        data = wf.readframes(CHUNK)

    stream.stop_stream()
    stream.close()

    p.terminate()

</code>

If the playback is garbled, try the instructions [here](http://tux-is-gaming.blogspot.com/2014/02/fixing-alsa-lib-pcmc7843sndpcmrecover.html) to fix PulseAudio.

Additional Tools
----------------

### Python

-   <https://www.reddit.com/r/Python/comments/31viu3/why_pip_doesnt_have_a_command_to_upgrade_all/>

pip list --outdated | cut -d ' ' -f1 | xargs -n1 pip install -U

scikit-learn for machine learning: pip install sklearn

[Category:Linux](/Category:Linux "wikilink")