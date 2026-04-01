from rdkit import Chem

# SMILES of Doxorubicin (Isomeric SMILES needed for R/S stereochemistry)
smiles = "C[C@H]1[C@H]([C@H](C[C@@H](O1)O[C@H]2C[C@@](CC3=C2C(=C4C(=C3O)C(=O)C5=C(C4=O)C(=CC=C5)OC)O)(C(=O)CO)O)N)O"

# Create molecule object
mol = Chem.MolFromSmiles(smiles)

# Assign stereochemistry
Chem.AssignStereochemistry(mol, force=True, cleanIt=True)

# Find chiral centers
chiral_centers = Chem.FindMolChiralCenters(mol, includeUnassigned=True)

# Print results
print("Chiral Centers (Atom Index, Configuration):")
for center in chiral_centers:
    print(center)

# Total number of chiral centers
print("\nTotal number of chiral centers:", len(chiral_centers))
