# sphinx Lexer

## conf.py

add

    from pygments.lexer import RegexLexer
    from pygments import token
    from sphinx.highlighting import lexers

    class LSDYNA_Lexer(RegexLexer):
        name = 'lsdyna'

        tokens = {
            'root': [
                (r'^\*.*?$', token.Keyword),
                (r'\$.*?$', token.Comment.Singleline),
                (r'(\d+\.\d*|\d*\.\d+)([eE][+-]?[0-9]+)?j?', token.Number.Float),
                (r'\d+j?', token.Number.Integer),
                (r'\&\w{2,9}|\&\w*?\s', token.Name),
                (r'\s', token.Text)
            ],
        }

    lexers['lsdyna'] = LSDYNA_Lexer(startinline=True)
