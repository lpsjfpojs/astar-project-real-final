using UnityEngine;

public class BlockPlacer : MonoBehaviour
{
    public GameObject wallPrefab;
    public GameObject columnPrefab;
    public GameObject beamPrefab;

    private GameObject selectedPrefab;

    void Update()
    {
        if (Input.GetMouseButtonDown(0) && selectedPrefab != null)
        {
            PlaceBlock();
        }
    }

    public void SetSelectedBlock(GameObject blockPrefab)
    {
        selectedPrefab = blockPrefab;
    }

    void PlaceBlock()
    {
        Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
        RaycastHit hit;

        if (Physics.Raycast(ray, out hit))
        {
            Instantiate(selectedPrefab, hit.point, Quaternion.identity);
        }
    }
}
