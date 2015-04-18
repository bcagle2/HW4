# Add a declarative step here for populating the DB with movies.

Given /the following movies exist/ do |movies_table|
  movies_table.hashes.each do |movie|
    # each returned element will be a hash whose key is the table header.
    # you should arrange to add that movie to the database here.
    Movie.create! movie
  end
end

# Make sure that one string (regexp) occurs before or after another one
#   on the same page


Then /I should see "(.*)" before "(.*)"/ do |e1, e2|
  #  ensure that that e1 occurs before e2.
  #  page.body is the entire content of the page as a string.
  assert_match(/#{e1}.*#{e2}/m, page.body)
end

# Make it easier to express checking or unchecking several boxes at once
#  "When I uncheck the following ratings: PG, G, R"
#  "When I check the following ratings: G"


When /I (un)?check the following ratings: (.*)/ do |uncheck, rating_list|
  # HINT: use String#split to split up the rating_list, then
  #   iterate over the ratings and reuse the "When I check..." or
  #   "When I uncheck..." steps in lines 89-95 of web_steps.rb
  #debugger
  rating_list.split(',').each do |rating|
    uncheck ? uncheck("ratings_#{rating}") : check("ratings_#{rating}")
  end
end

Then /I should see all the movies/ do
  # Make sure that all the movies in the app are visible in the table

  rows = page.all('table#movies tbody tr').length
  rows.should eq Movie.count


  #debugger
  #page.body.should =~ ('table#movies tbody tr').length
  #rows.should eq Movie.count



  # Make sure that all the movies in the app are visible in the table
  #flunk "Unimplemented"

  #Movie.find(:all).length.should page.body.scan(/<tr>/).length
  #Movie.find(:all).length == page.body.scan(/<tr>/).length


#  debugger
#  Movie.all.each do |movie|
#    content = page.body
#    abc = page.body
#    index_title = content.index(movie.title)
#    assert_equal true, index_title != nil
#  end


#  movies = Movie.all
#  movies.each do |movie|
#    if page.respond_to? :should
#      page.should have_content(movie.title)
#    else
#      assert page.has_content?(movie.title)
#    end
#  end

#  Movie.find(:all).count.should == page.all('table tbody tr').count

#debugger
#Movie.find(:all).length.should page.body.scan(/<tr>/).length
#Movie.find(:all).length == page.body.scan(/<tr>/).length


#assert all( "table#movies tbody tr").count==10

#debugger
#html = Capybara::Node::Simple.new(body)
#tbody = Capybara::Node::Simple.new(tbody)
#dumvar = page.body
#tr = Capybara::Node::Simple.new(tr)
#dumvar = page.body
#table = Capybara::Node::Element.new(table)
#dumvar = page.body
#mov1 = Capybara::Node::Element.new(movies)

#dumvar = page.body 

#rows = html.find("table#selector").all('tr')
#table = rows.map { |r| r.all('th,td').map { |c| c.text.strip } }
#pge = page
#body = page.body

#all = page.all
#body = page.body
#rows equals page.all("table#movies tbody tr td[1]").map! {|t| t.text}

#  movies.each do |movie|
#    page.body.should =~
#  end

#  Movie.all.each do |movie|
#    page.find("#table").should have_content(movie.title)
#  end
end


Then /^the director of "(.*?)" should be "(.*?)"$/ do |movie_title, new_director|
  movie = Movie.find_by_title movie_title
  movie.director.should == new_director
end
