
void ordenar(int c[], char n[][50], char ed[][50], int ej[]) {
	
	int k, j, auxC, auxEJ;
	char auxN[50], auxED[50];
		for(k=1; k<cont; k++) {
			for(j=0; j<cont-k; j++) {
				if(strcmp(n[j], n[j+1])>0) {
					auxC= c[j];
					c[j]= c[j+1];
					c[j+1]= auxC;

					auxEJ= ej[j];
					ej[j]= ej[j+1];
					ej[j+1]= auxEJ;

					strcpy(auxN, n[j]);
					strcpy(n[j], n[j+1]);
					strcpy(n[j+1], auxN);

					strcpy(auxED, ed[j]);
					strcpy(ed[j], ed[j+1]);
					strcpy(ed[j+1], auxED);
				}
			}
		}
}




void consultagen(int c[], char n[][50], char ed[][50], int ej[]) {

	int x;

	for(x=0; x<cont; x++) {
		printf("Clave: %d\n", c[x]);
		printf("Título: %s\n", n[x]); 
		printf("Editorial: %s\n", ed[x]);
		printf("Ejemplares: %d\n\n\n", ej[x]);
	}

}

int buscar(int c[], int b) {

	int pos= -1, x;
	for(x=0; x<cont; x++) {
		if(c[x]==b){
			pos= x; }

	}

	return pos;
}


void consultaesp(int c[], char n[][50], char ed[][50], int ej[], int b) {

		printf("\nClave: %d", c[b]);
		printf("\nTítulo: %s", n[b]);
		printf("\nEditorial: %s", ed[b]);
		printf("\nEjemplares: %d\n\n", ej[b]);
	}


void modificar(int c[], char n[][50], char ed[][50], int ej[], int b) {

	int opc;

	printf("Datos actuales: \n"
		"Clave: %d\n"
		"Título: %s\n"
		"Editorial: %s\n"
		"Ejemplares: %d\n\n", c[b], n[b], ed[b], ej[b]);


	do {
	printf("¿Modificar?\n"
		"1) Clave\n"
		"2) Título\n"
		"3) Editorial\n"
		"4) Ejemplares disponibles\n"
		"5) Todo\n"
		"6)Salir\n > ");
	scanf("%d", &opc);

	switch(opc) {

		case 1: 
				printf("Nueva clave: ");
				scanf("%d", &c[b]);
				break;

		case 2:
				printf("Nuevo nombre: ");
				fflush(stdin);
				gets(n[b]);
				break;

		case 3: 
				printf("Nueva editorial: ");
				fflush(stdin);
				gets(ed[b]);
				break;

		case 4: 
				printf("Ejemplares disponibles: ");
				scanf("%d", &ej[b]);
				break;

		case 5:
				printf("Nueva clave: ");
				scanf("%d", &c[b]);
				printf("Nuevo nombre: ");
				fflush(stdin);
				gets(n[b]);
				printf("Nueva editorial: ");
				fflush(stdin);
				gets(ed[b]);
				printf("Ejemplares disponibles: ");
				scanf("%d", &ej[b]);
				break;

		}
		
		system("cls");
	printf("Datos actualizados: \n"
		"Clave: %d\n"
		"Título: %s\n"
		"Editorial: %s\n"
		"Ejemplares: %d\n\n", c[b], n[b], ed[b], ej[b]);
	} while(opc!=6);
}	



void eliminar(int c[], char n[][50], char ed[][50], int ej[], int b) {

	int i;

	for (i=b; i<cont; i++) {
		c[i]= c[i+1];
		strcpy(n[i], n[i+1]);
		strcpy(ed[i], ed[i+1]);
		ej[i]= ej[i+1];
		cont--;
	}
}


void repeticion(int c[]) {

	int x;

	for(x=0; x<cont; x++) {
		if(c[cont]==c[x]) {
			system("color 04");
			printf("Clave de libro repetida, intente de nuevo.\n");
			system("color 0F");
			printf("Nueva clave: ");
			scanf("%d", &c[cont]);}
	}
}
				
