## Invoice Exchange

The InvoiceExchange is a Rails 4.2.2 app using Ruby 2.2.0 and deployed to Heroku.

## Development

### Setup

1. Get the code

        % git clone https://github.com/haojin111/forecast.git
    
2. Set up your environment

        % bin/setup
    
3. Ask for environment variables and update your `.env`

        % vim .env
  
4. Start Foreman

        % foreman start

5. Verify the app is up and running

        % open http://localhost:5000
  
### Protocol

1. Look for cards in the **Next Up** list.
2. When you start a card, add yourself and move the card to the **In Progress**
   list.
3. When opening a pull request, move the card to the **Code Review** list and
   ask in Slack for a review.
4. Once the review is complete, merge into master as usual. Wait for CI to
   finish running the build.
5. Once CI is finished running the build, it will deploy to staging. Move the
   card to **On Staging for acceptance** at this time. Comment on the card with
  acceptance instructions. Include a URL to staging. Ask in Slack for
  acceptance.

### Ongoing

* Run test suite before committing to the master branch.

        % rake

* Dump production data into your local db. (Note that you need to drop your
  local database first).

        % rake db:drop
        % heroku pg:pull DATABASE_URL invoice_exchange_development -r production
        
### Deployment

        % git push staging master
        
        % git push production master
        
### Sending email on staging

*TODO: add email interceptor and detail instructions on how to set up*

### Admin Access

After running `bin/setup`, two admin users should have been created. You can
find their login credentials in `lib/tasks/admin_users.rake`.

If not, you can try and run the rake task again.

        % rake admin:create_admin_users
