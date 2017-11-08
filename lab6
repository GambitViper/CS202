function parseEmail( email ){
    var email_obj = {username : '', domain: ''};
    var parse = email.split('@');
    if(email.indexOf('@') == -1 || parse[0] == '' || parse[1] == ''){
        return undefined;
    }
    email_obj.username = parse[0];
    email_obj.domain = parse[1];
    return email_obj;
}

function winners( game ){
    var winners_list = [];
    for(var i = 0; i < game.length; i++){
        var home = game[i].home;
        var away = game[i].away;
        if(home.score > away.score){
            winners_list.push(home.name);
        }else if(home.score == away.score){
            winners_list.push('tie');
        }else {
            winners_list.push(away.name);
        }
    }
    return winners_list;
}

function rank( votes ){
    var candidates = [];
    for(var i = 0; i < votes.length; i++){
        var name = votes[i].toLowerCase();
        var indexIfExists = -1;
        for(var j = 0; j < candidates.length; j++){
            if(candidates[j][0] == name){
                indexIfExists = j;
            }
        }
        if(indexIfExists == -1){
            var voter_data = [ name, 1];
            candidates.push(voter_data);
        }else {
            candidates[indexIfExists][1]++;
        }
    }
    candidates = sort(candidates);
    return candidates;
}

function sort( aggregate ){
    var sorted = [];
    var len = aggregate.length;
    do{
        var swapped = false;
        for(var i = 1; i < len; i++){
            if(aggregate[i-1][1] < aggregate[i][1]){
                swap(i-1, i);
                swapped = true;
            }
        }
        len -= 1;
    }while(swapped);
    function swap( first, second ){
        var temp = aggregate[first];
        aggregate[first] = aggregate[second];
        aggregate[second] = temp;
    }
    for(var j = 0; j < aggregate.length; j++){
        sorted.push(aggregate[j][0]);
    }
    return sorted;
}
