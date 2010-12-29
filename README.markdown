API Correios
============

Installation
============
If you have _setuptools_ you can use 
    $ easy_install -U pycorreios
Otherwise, you can download the source from [GitHub][git] and run 
    $ python setup.py install

[git]: https://github.com/avelino/pycorreios "PyCorreios"

Examples
========
Some simple examples of what pyCorreios code looks like:
    # -*- coding: utf-8 -*-
    from pycorreios import Correios

    frete = Correios().frete(Correios().SEDEX,'44001535','03971010',10,18,8)
    if frete['Erro'] != '0':
        print 'Deu erro! :('
        print frete['Erro']
        print frete['MsgErro']
    else:
        print "Valor: R$%s\nPrazo de Entrega: %s" % (frete['Valor'],frete['PrazoEntrega'])

    print

    cep = Correios().cep('03971010')
    for tag_name in cep.keys():
        print tag_name + ': ' + cep[tag_name]

    encomenda = Correios().encomenda('SW238151411BR')
    for status in encomenda:
        print 'Data: ' + status.data
        print 'Local: ' + status.local
        print 'Status: ' + status.status
        try:
            print 'Descricao: ' + status.descricao
        except:
            pass
        print '----------------------'
