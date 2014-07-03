# Mess Organizer

Organize your desktop, downloads and other messy folders with a simple rake command. Easy and effective.

## Usage

You will need [Ruby](https://www.ruby-lang.org/en/installation/) and [Rake](https://rubygems.org/gems/rake) installed on your OS before you start using the Mess Organizer. If you have the Rake gem already installed, just clone this repo to the folder you want to organize and run "rake". 

In the following example, let's organize a typical messy download folder:

```
$ cd ~/Downloads
$ git clone https://github.com/tiagopog/mess_organizer.git
$ rake --rakefile mess_organizer/Rakefile
```

1. The "Downloads" folder before organizing it:

![The messy "Downloads" folder](https://s3-us-west-2.amazonaws.com/mess-organizer/image_1.jpg)

2. Running the "rake" command. Note that it displays where each file/folder is being placed:

![Rake in action](https://s3-us-west-2.amazonaws.com/mess-organizer/image_2.jpg)

3. Done! Now you have a brand new organized folder with your files under the "stuff":

![Voilà! That's how you folder will look like now](https://s3-us-west-2.amazonaws.com/mess-organizer/image_3.jpg)

## Contributing

1. Fork it;
2. Create your feature branch (`git checkout -b my-new-feature`);
3. Commit your changes (`git commit -am 'Add some feature'`);
4. Push to the branch (`git push origin my-new-feature`);
5. Create new Pull Request.
