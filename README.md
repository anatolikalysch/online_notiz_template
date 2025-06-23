# online_notiz_template

**online_notiz_template** is a mock project designed for educational purposes to illustrate a realistic software supply chain. It includes frontend and backend folders with simulated source code and dependencies and is intended for generating and analyzing Software Bill of Materials (SBOM) using open source tools.

> **Note:** This is not a functional application and is not intended for execution or deployment. It serves purely as a reference example for software supply chain analysis.

---

## Structure

- `frontend/` - React-based mock frontend with `package.json`
- `backend/` - Express-based mock backend with `package.json`
- `Dockerfile` - Example container build script
- `.gitignore`, `README.md`, `LICENSE` - Standard project files

---

## SBOM Generation Instructions (Using Syft)

You can use the open source tool **[Syft](https://github.com/anchore/syft)** to generate a Software Bill of Materials for this project.

### Step 1: Install Syft

**macOS / Linux:**
```bash
curl -sSfL https://raw.githubusercontent.com/anchore/syft/main/install.sh | sh -s -- -b /usr/local/bin
```

**Windows (PowerShell):**
```powershell
iwr -useb https://raw.githubusercontent.com/anchore/syft/main/install.ps1 | iex
```

**Docker alternative:**
```bash
docker run --rm -v $PWD:/work -w /work anchore/syft:latest dir:./online_notiz_template
```

---

### Step 2: Navigate to the Project Directory

After unzipping the repo:
```bash
cd online_notiz_template
```

---

### Step 3: Generate the SBOM

**SPDX JSON Format:**
```bash
syft dir:. --scope all-layers -o spdx-json > sbom.spdx.json
```

**CycloneDX JSON Format:**
```bash
syft dir:. -o cyclonedx-json > sbom.cyclonedx.json
```

**Optional Table Format (for CLI viewing):**
```bash
syft dir:. -o table
```

---

### Step 4: Explore the SBOM

You can view or import the generated SBOM files into:

- [Dependency-Track](https://dependencytrack.org/)
- [CycloneDX Visualizer](https://cyclonedx.org/tool-center/)
- SBOM Viewer Extensions in VS Code

---

## Educational Use

Use this repository to:
- Practice generating SBOMs
- Explore JavaScript/Node.js dependencies
- Teach or learn about software supply chain security

---

## License

This project is provided under the [MIT License](LICENSE).
