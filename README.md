web2py_ckeditor
===============

Plugin to add ckeditor to web2py apps ( based on the original https://bitbucket.org/PhreeStyle/web2py_ckeditor/wiki/Home)

I added some changes and included some features.


== CKEditor Plugin for web2py ==

=== Introduction ===

Sometimes you just need a WYSIWYG editor. This plugin integrates CKEditor into web2py. It acts much like the Auth object in its usage. For example, in your model, you need to import and initialize it:

{{{
#!python

from plugin_ckeditor import CKEditor
ckeditor = CKEditor(db)
ckeditor.define_tables()

}}}

=== Basic Usage ===

It's most basic usage is to assign it to a Field widget:

{{{
#!python

db.define_table('content',
    Field('title', length=255),
    Field('public', 'boolean', default=True),
    Field('text', 'text', widget=ckeditor.widget)
)

}}}

The CKEditor now automatically becomes available every time SQLFORM is used. This is a screen shot of it in action:

{{https://lh4.googleusercontent.com/-HLLFte_tXCw/ThclwgF-TtI/AAAAAAAAAC8/cu3qqcUuDeE/Screen%252520shot%2525202011-07-08%252520at%25252011.01.36%252520AM.png|Main Window}}

This is great by itself, however, I decided to take it a few steps further. First of all, also supports edit in place. This is a test page to demonstrate:

{{https://lh4.googleusercontent.com/-bsWPwiuQg20/Thcl_C0sraI/AAAAAAAAADE/73qIJK9_OS8/Screen%252520shot%2525202011-07-08%252520at%25252011.02.06%252520AM.png|Result}}

To make this content editable, all it takes is the following line in the view:

{{{
#!python

{{=ckeditor.edit_in_place('.editable', URL())}}

}}}

This makes any element with the 'editable' class editable in place. It also requires a URL to save the data to when the save button is clicked. Here's what it looks like in edit mode:

{{https://lh3.googleusercontent.com/-9kv2lFa4JjA/ThcmcWAGF5I/AAAAAAAAADM/UAwhM6LxoeQ/Screen%252520shot%2525202011-07-08%252520at%25252011.02.16%252520AM.png|Edit in Place}}

It is all AJAX enabled, spellchecks as you type, and it's fast. Edit in place is another great feature, but I also took it a step further than that and integrated upload and browse functionality for images and Flash movies:

{{https://lh4.googleusercontent.com/-XtkEW2sXXyU/Thcm-IwkZ8I/AAAAAAAAADU/uyPo2FTMob0/Screen%252520shot%2525202011-07-08%252520at%25252011.33.28%252520AM.png|Image Properties}}

{{https://lh3.googleusercontent.com/-mBjk0bs_-Z8/ThcnEixpCDI/AAAAAAAAADc/_xH6sWwgs6o/Screen%252520shot%2525202011-07-08%252520at%25252011.35.29%252520AM.png|Image Info}}

{{https://lh5.googleusercontent.com/-M4ddg9Dz9Kg/ThcnH0dubEI/AAAAAAAAADk/9WzdPj1ZiVE/Screen%2Bshot%2B2011-07-08%2Bat%2B11.35.06%2BAM.png|Browse Images}}

{{https://lh4.googleusercontent.com/-8DKGzp3qqbs/ThcnV3GNCOI/AAAAAAAAADs/A6_-CGOM8-g/Screen%252520shot%2525202011-07-08%252520at%25252011.35.42%252520AM.png|Image Upload Result}}

The upload and browse functionality is all taken care of by the plugin and does not require you to do anything on your end once you have initialized the plugin in your model as demonstrated above.

=== References ===

I used the following resources in developing this plugin, so a special thanks to the authors of these for providing the ground work required to make this possible:

http://www.web2pyslices.com/main/slices/take_slice/18

http://www.bitsntuts.com/jquery/ckeditor-edit-in-place-jquery-plugin