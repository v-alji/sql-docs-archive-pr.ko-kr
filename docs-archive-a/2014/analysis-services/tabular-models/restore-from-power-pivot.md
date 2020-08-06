---
title: PowerPivot에서 복원 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dbb0e7867451e67eaa1503c54d7e3da1c276965
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738829"
---
# <a name="restore-from-powerpivot"></a><span data-ttu-id="ded37-102">PowerPivot에서 복원</span><span class="sxs-lookup"><span data-stu-id="ded37-102">Restore from PowerPivot</span></span>
  <span data-ttu-id="ded37-103">SQL Server Management Studio의 PowerPivot 기능에서 복원을 사용하여 테이블 형식 모드에서 실행되는 Analysis Services 인스턴스에서 새 테이블 형식 model 데이터베이스를 만들거나 PowerPivot 통합 문서(.xlsx)에서 기존 데이터베이스를 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-103">You can use the Restore from PowerPivot feature in SQL Server Management Studio to create a new Tabular model database on an Analysis Services instance (running in Tabular mode), or restore to an existing database from a PowerPivot workbook (.xlsx).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ded37-104">SQL Server Data Tools의 PowerPivot 프로젝트 템플릿에서 가져오기가 비슷한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-104">The Import from PowerPivot project template in SQL Server Data Tools provides similar functionality.</span></span> <span data-ttu-id="ded37-105">자세한 내용은 [PowerPivot에서 가져오기 &#40;SSAS 테이블 형식&#41;](import-from-power-pivot-ssas-tabular.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ded37-105">For more information, see [Import from PowerPivot &#40;SSAS Tabular&#41;](import-from-power-pivot-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="ded37-106">PowerPivot에서 복원을 사용할 때는 다음 사항에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-106">When using Restore from PowerPivot, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="ded37-107">PowerPivot에서 복원을 사용하려면 Analysis Services 인스턴스에서 서버 관리자 역할의 멤버로 로그인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-107">In order to use Restore from PowerPivot, you must be logged on as a member of the Server Administrators role on the Analysis Services instance.</span></span>  
  
-   <span data-ttu-id="ded37-108">Analysis Services 인스턴스 서비스 계정은 복원할 통합 문서 파일에 대한 읽기 권한을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-108">The Analysis Services instance service account must have Read permissions on the workbook file you are restoring from.</span></span>  
  
-   <span data-ttu-id="ded37-109">기본적으로, PowerPivot에서 데이터베이스를 복원하는 경우 테이블 형식 model 데이터베이스 데이터 원본 가장 정보 속성이 Analysis Services 인스턴스 서비스 계정을 지정하는 기본값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-109">By default, when you restore a database from PowerPivot, the Tabular model database Data Source Impersonation Info property is set to Default, which specifies the Analysis Services instance service account.</span></span> <span data-ttu-id="ded37-110">가장 자격 증명을 데이터베이스 속성의 Windows 사용자 계정으로 변경하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-110">It is recommended you change the impersonation credentials to a Windows user account in Database Properties.</span></span> <span data-ttu-id="ded37-111">자세한 내용은 [가장&#40;SSAS 테이블 형식&#41;](impersonation-ssas-tabular.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ded37-111">For more information, see [Impersonation &#40;SSAS Tabular&#41;](impersonation-ssas-tabular.md).</span></span>  
  
-   <span data-ttu-id="ded37-112">PowerPivot 데이터 모델의 데이터는 Analysis Services 인스턴스의 기존 또는 새 테이블 형식 model 데이터베이스로 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-112">Data in the PowerPivot data model will be copied into an existing or new Tabular model database on the Analysis Services instance.</span></span> <span data-ttu-id="ded37-113">PowerPivot 통합 문서에 연결된 테이블이 있는 경우 해당 테이블은 데이터 원본을 사용하지 않고 새 테이블에 붙여넣기를 사용하여 만드는 테이블과 비슷한 테이블로 다시 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-113">If your PowerPivot workbook contains linked tables, they will be recreated as a table without a data source, similar to a table created using Paste To New table.</span></span>  
  
### <a name="to-restore-from-powerpivot"></a><span data-ttu-id="ded37-114">PowerPivot에서 복원하려면</span><span class="sxs-lookup"><span data-stu-id="ded37-114">To Restore from PowerPivot</span></span>  
  
1.  <span data-ttu-id="ded37-115">SSMS의 복원 하려는 Active Directory 인스턴스에서 **데이터베이스**를 마우스 오른쪽 단추로 클릭 한 다음 **PowerPivot에서 복원**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-115">In SSMS, in the Active Directory instance you want to restore to, right click **Databases**, and then click **Restore from PowerPivot**.</span></span>  
  
2.  <span data-ttu-id="ded37-116">**PowerPivot에서 복원** 대화 상자의 **복원 원본**에 있는 **백업 파일**에서 **찾아보기**를 클릭한 다음 복원할 .abf 또는 .xslx 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-116">In the **Restore from PowerPivot** dialog box, in **Restore Source**, in **Backup file**, click **Browse**, and then select an .abf or .xslx file to restore from.</span></span>  
  
3.  <span data-ttu-id="ded37-117">**대상 복원**의 **데이터베이스 복원**에 새 데이터베이스 또는 기존 데이터베이스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-117">In **Restore Target**, in **Restore database**, type a name for a new database or for an existing database.</span></span> <span data-ttu-id="ded37-118">이름을 지정하지 않으면 통합 문서의 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-118">If you do not specify a name, the name of the workbook is used.</span></span>  
  
4.  <span data-ttu-id="ded37-119">**스토리지 위치**에서 **찾아보기**를 클릭한 다음 데이터베이스를 저장할 위치를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-119">In **Storage location**, click **Browse**, and then select a location to store the database.</span></span>  
  
5.  <span data-ttu-id="ded37-120">**옵션**에서 **보안 정보 포함** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-120">In **Options**, leave **Include security information** checked.</span></span> <span data-ttu-id="ded37-121">PowerPivot 통합 문서에서 복원할 때 이 설정은 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ded37-121">When restoring from a PowerPivot workbook, this setting does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded37-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ded37-122">See Also</span></span>  
 <span data-ttu-id="ded37-123">[테이블 형식 모델 데이터베이스 &#40;SSAS 테이블 형식&#41;](tabular-model-databases-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="ded37-123">[Tabular Model Databases &#40;SSAS Tabular&#41;](tabular-model-databases-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="ded37-124">PowerPivot &#40;SSAS 테이블 형식&#41;에서 가져오기</span><span class="sxs-lookup"><span data-stu-id="ded37-124">Import from PowerPivot &#40;SSAS Tabular&#41;</span></span>](import-from-power-pivot-ssas-tabular.md)  
  
  
