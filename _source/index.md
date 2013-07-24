---
layout : layout
title : Chris Dury Blog
---
@model Pretzel.Logic.Templating.Context.PageContext

<div class="posts">
@{
    var numberPosts = 1;
}
    @for (var i = 0; i < numberPosts && i < Model.Site.Posts.Count; i++)
    {
        var post = Model.Site.Posts[i];
            <div class="idea">
                @if (i == 0 && post.Layout == "post")
                {
					<h2>@post.Title</h2>                    
                    @Raw(post.Content)
                    <div class="postdate">@post.Date.ToString("d MMM, yyyy")</div>
					<div>
                        <ul>
                            @foreach(var tag in post.Tags)
                            {
                                <li><a href="/tag/@tag">@tag</a></li>
                            }
                        </ul>
                    </div>
                }
                else
                {
                    <h2><a class="postlink" href="@post.Url">@post.Title</a></h2>
                    <div class="postdate">@post.Date.ToString("d MMM, yyyy")
                        <ul>
                            @foreach (var tag in post.Tags)
                            {
                                <li><a href="/tag/@tag">@tag</a></li>
                            }
                        </ul>
                    </div>
                }
            </div>
    }
</div>


<h3>OLDER</h3>
<ul class="postArchive">
@foreach(var post in Model.Site.Posts.Skip(numberPosts))
{
    <li>
        <span class="olderpostdate">@post.Date.ToString("d-MM")</span> <a class="postlink" href="@post.Url">@post.Title</a>
    </li>
}
</ul>
