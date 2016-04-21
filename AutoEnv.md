To actiavte environment variables
----------------------------------

    mkdir test
    mkvirtualenv test
    pip install autoenv
    touch test/.env
    echo "echo 'woah'" > test/.env
    cd test
    woah
    
If it's not working it might be due to the virtualenv, try:

    source /home/[username]/.virtualenvs/test/bin/activate.sh
