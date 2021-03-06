# will_paginate

will_paginate is a pagination library that integrates with Ruby on Rails, Sinatra, Merb, DataMapper and Sequel.

Installation:

``` ruby
## Gemfile for Rails 3, Rails 4, Sinatra, and Merb
gem 'will_paginate', '~> 3.0'
```

See [installation instructions][install] on the wiki for more info.


## Basic will_paginate use

``` ruby
## perform a paginated query:
@posts = Post.paginate(:page => params[:page])

# or, use an explicit "per page" limit:
Post.paginate(:page => params[:page], :per_page => 30)

## render page links in the view:
<%= will_paginate @posts %>

## render remote page links in view:
<%= will_paginate @posts, remote: true %>
```

And that's it! You're done. You just need to add some CSS styles to [make those pagination links prettier][css].

You can customize the default "per_page" value:

``` ruby
# for the Post model
class Post
  self.per_page = 10
end

# set per_page globally
WillPaginate.per_page = 10
```

New in Active Record 3:

``` ruby
# paginate in Active Record now returns a Relation
Post.where(:published => true).paginate(:page => params[:page]).order('id DESC')

# the new, shorter page() method
Post.page(params[:page]).order('created_at DESC')
```

See [the wiki][wiki] for more documentation. [Ask on the group][group] if you have usage questions. [Report bugs][issues] on GitHub.

Happy paginating.


[wiki]: https://github.com/mislav/will_paginate/wiki
[install]: https://github.com/mislav/will_paginate/wiki/Installation "will_paginate installation"
[group]: http://groups.google.com/group/will_paginate "will_paginate discussion and support group"
[issues]: https://github.com/mislav/will_paginate/issues
[css]: http://mislav.uniqpath.com/will_paginate/
