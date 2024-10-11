import 'package:flutter/material.dart';

void main() {
  runApp(DesembargaTreinoApp());
}

class DesembargaTreinoApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Desembarga Treino',
      theme: ThemeData(
        primarySwatch: Colors.green,
      ),
      home: TelaPrincipal(),
    );
  }
}

class TelaPrincipal extends StatelessWidget {
  final List<String> treinos = [
    'Peito e Tríceps',
    'Costas e Bíceps',
    'Pernas e Ombros',
    'Cardio',
    'Treino Completo'
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Desembarga Treino'),
      ),
      body: ListView.builder(
        itemCount: treinos.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(treinos[index]),
            onTap: () {
              Navigator.push(
                context,
                MaterialPageRoute(
                  builder: (context) => DetalhesTreino(treino: treinos[index]),
                ),
              );
            },
          );
        },
      ),
    );
  }
}

class DetalhesTreino extends StatelessWidget {
  final String treino;

  DetalhesTreino({required this.treino});

  final Map<String, List<String>> exercicios = {
    'Peito e Tríceps': ['Supino Reto', 'Crucifixo Inclinado', 'Tríceps no Pulley'],
    'Costas e Bíceps': ['Puxada Alta', 'Remada Curvada', 'Rosca Direta'],
    'Pernas e Ombros': ['Agachamento Livre', 'Leg Press', 'Desenvolvimento com Halteres'],
    'Cardio': ['Corrida', 'Bicicleta', 'Elíptico'],
    'Treino Completo': ['Supino', 'Agachamento', 'Remada Curvada', 'Corrida']
  };

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Treino: $treino'),
      ),
      body: ListView.builder(
        itemCount: exercicios[treino]!.length,
        itemBuilder: (context, index) {
          return ListTile(
            title: Text(exercicios[treino]![index]),
          );
        },
      ),
    );
  }
}
