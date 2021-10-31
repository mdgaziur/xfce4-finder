### This is a fork of https://github.com/godlikemouse/xfce4-finder

## Xfce4-finder
Smart and intuitive application finder, complete with theme and customization support.

![Screenshot](https://github.com/mebesus/xfce4-finder/blob/master/res/ss.png)

## Key Features
- Blazingly fast realtime application finding
- Inline application argument launching using tab: Begin by typing an application name, hit TAB_KEY to lock it in, begin typing arguments to that application
- Customizable UI using CSS
- Intuitive Web/Desktop Integration: Just type what you're looking for, the application itself will determine whether or not an application should be launched or if the context requires an online web search.
- Direct command invocation: Utilize terminal commands directly by typing the executable name
- Supports tab autocompletion
- Supports CONTROL_KEY + ENTER_KEY for domain name completion *(ie. google => www.google.com, google.com => www.google.com, www.google => www.google.com)*.

## Fork Patches
- Removed application description
- Automatically close the application when it loses focus

## Customizable Settings <a name="customizable-settings"></a>
Application settings can be controlled using xfconf-query.

Available settings:
- /file-extension - defaults to ".desktop", controls the filenames to use for parsing.
- /web-search - defaults to "https://www.google.com/#safe=on&q=%s", controls the url format to use when applying a web search, %s is replaced by the query to be used.
- /theme = defaults to "default", controls the CSS file to use for the application *(Default location is: ~/.config/xfce4/finder/default.css)*.
- /application-directories - defaults to /usr/share/applications and ~/.local/share/applications, specifies the directories in which to look for application files with matching /file-extension.

List all available settings:

    xfconf-query -c xfce4-finder -l

List a setting:

    xfconf-query -c xfce4-finder -p /web-search

Change a setting:

    xfconf-query -c xfce4-finder -p /web-search -s https://www.bing.com?q=%s

Set array values:

	xfconf-query -c xfce4-finder -p /application-directories -s /usr/share/applications -s /usr/local/share/applications

The above sets the application-directories array property which is used by xfce4-finder to location application files to /usr/share/applications and /usr/local/share/applications.  You may need to update this setting if your applications directory is not included by default.

## Building
To build the application you will need to have the following dependencies installed.
- [Glib 2.0](https://developer.gnome.org/glib/)
- [Gio 2.0](https://developer.gnome.org/gio/)
- [Gtkmm 3.0](http://www.gtkmm.org/en/)
- [Garcon](http://www.linuxfromscratch.org/blfs/view/svn/xfce/garcon.html)
- [libxfconf](http://www.linuxfromscratch.org/blfs/view/systemd/xfce/xfconf.html)
- [libxfce4util](http://www.linuxfromscratch.org/blfs/view/7.9/xfce/libxfce4util.html)
- [libxfce4ui](http://www.linuxfromscratch.org/blfs/view/systemd/xfce/libxfce4ui.html)
- [automake](https://www.gnu.org/software/automake/)
- [autoconf](https://www.gnu.org/software/autoconf/autoconf.html)
- [xfce4-dev-tools](http://www.xfce.org/)

Building the application:

    cd xfce4-finder/
    ./autogen.sh
    make
    make install

## Running
After successfully installing xfce4-finder, simply type ``xfce4-finder`` on terminal to run it. You may wish to add a keybinding for it

## License
xfce4-finder is released under the MIT License.
