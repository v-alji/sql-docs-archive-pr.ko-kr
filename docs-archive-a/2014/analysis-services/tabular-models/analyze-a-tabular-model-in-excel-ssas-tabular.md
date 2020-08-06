---
title: Excel에서 테이블 형식 모델 분석 (SSAS 테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
author: minewiskan
ms.author: owend
ms.openlocfilehash: fae542ffb5b470d23d9cf27fcc11367f571e7cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653524"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a><span data-ttu-id="a8c07-102">Excel에서 테이블 형식 모델 분석(SSAS 테이블 형식)</span><span class="sxs-lookup"><span data-stu-id="a8c07-102">Analyze a Tabular Model in Excel (SSAS Tabular)</span></span>
  <span data-ttu-id="a8c07-103">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 의 Excel에서 분석 기능은 Microsoft Excel을 열고 모델 작업 영역 데이터베이스에 데이터 원본을 연결한 후 워크시트에 피벗 테이블을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-103">The Analyze in Excel feature in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] opens Microsoft Excel, creates a data source connection to the model workspace database, and adds a PivotTable to the worksheet.</span></span> <span data-ttu-id="a8c07-104">피벗 테이블 필드 목록에 모델 개체(테이블, 열, 측정값, 계층 및 KPI)가 필드로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-104">Model objects (tables, columns, measures, hierarchies, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8c07-105">Excel에서 분석 기능을 사용하려면 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]를 실행하는 컴퓨터에 Microsoft Office 2003 이상 버전이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-105">To use the Analyze in Excel feature, you must have Microsoft Office 2003 or later installed on the same computer as [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="a8c07-106">컴퓨터에 Office가 설치되어 있지 않을 경우 다른 컴퓨터의 Excel을 사용하여 데이터 원본으로 모델 작업 영역 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-106">If Office is not installed on the same computer, you can use Excel on another computer and connect to the model workspace database as a data source.</span></span> <span data-ttu-id="a8c07-107">그런 다음 워크시트에 피벗 테이블을 수동으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-107">You can then manually add a PivotTable to the worksheet.</span></span> <span data-ttu-id="a8c07-108">피벗 테이블 필드 목록에 모델 개체(테이블, 열, 측정값 및 KPI)가 필드로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-108">Model objects (tables, columns, measures, and KPIs) are included as fields in the PivotTable field list.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="a8c07-109">작업</span><span class="sxs-lookup"><span data-stu-id="a8c07-109">Tasks</span></span>  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a><span data-ttu-id="a8c07-110">Excel에서 분석 기능을 사용하여 테이블 형식 모델 프로젝트를 분석하려면</span><span class="sxs-lookup"><span data-stu-id="a8c07-110">To analyze a tabular model project by using the Analyze in Excel feature</span></span>  
  
1.  <span data-ttu-id="a8c07-111">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 **모델** 메뉴를 클릭한 다음 **Excel에서 분석**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-111">In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], click the **Model** menu, and then click **Analyze in Excel**.</span></span>  
  
2.  <span data-ttu-id="a8c07-112">**자격 증명 및 큐브 뷰 선택** 대화 상자에서 다음 자격 증명 옵션 중 하나를 선택하여 모델 작업 영역 데이터 원본에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-112">In the **Choose Credential and Perspective** dialog box, select one of the following credential options to connect to the model workspace data source:</span></span>  
  
    -   <span data-ttu-id="a8c07-113">현재 사용자 계정을 사용하려면 **현재 Windows 사용자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-113">To use the current user account, select **Current Windows User**.</span></span>  
  
    -   <span data-ttu-id="a8c07-114">다른 사용자 계정을 사용하려면 **기타 Windows 사용자**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-114">To use a different user account, select **Other Windows User**.</span></span>  
  
         <span data-ttu-id="a8c07-115">일반적으로 이 사용자 계정은 역할의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-115">Typically, this user account will be a member of a role.</span></span> <span data-ttu-id="a8c07-116">암호는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-116">No password is required.</span></span> <span data-ttu-id="a8c07-117">이 계정은 작업 영역 데이터베이스에 대한 Excel 연결의 컨텍스트에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-117">The account can only be used in the context of an Excel connection to the workspace database.</span></span>  
  
    -   <span data-ttu-id="a8c07-118">보안 역할을 사용하려면 **역할**을 선택한 다음 목록 상자에서 하나 이상의 역할을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-118">To use a security role, select **Role**, and then in the listbox, select one or more roles.</span></span>  
  
         <span data-ttu-id="a8c07-119">보안 역할은 역할 관리자를 사용하여 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-119">Security roles must be defined using the Role Manager.</span></span> <span data-ttu-id="a8c07-120">자세한 내용은 [역할 만들기 및 관리&#40;SSAS 테이블 형식&#41;](roles-ssas-tabular.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c07-120">For more information, see [Create and Manage Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
3.  <span data-ttu-id="a8c07-121">큐브 뷰를 사용하려면 **큐브 뷰** 목록 상자에서 큐브 뷰를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-121">To use a perspective, in the **Perspective** listbox, select a perspective.</span></span>  
  
     <span data-ttu-id="a8c07-122">기본값이 아닌 큐브 뷰는 큐브 뷰 대화 상자를 사용하여 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-122">Perspectives (other than default) must be defined using the Perspectives dialog box.</span></span> <span data-ttu-id="a8c07-123">자세한 내용은 [SSAS 테이블 형식&#41;&#40;큐브 뷰 만들기 및 관리 ](perspectives-ssas-tabular.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8c07-123">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a8c07-124">모델 디자이너에서 모델 프로젝트를 변경해도 Excel의 피벗 테이블 필드 목록에 자동으로 반영되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-124">The PivotTable Field List in Excel does not refresh automatically as you make changes to the model project in the model designer.</span></span> <span data-ttu-id="a8c07-125">피벗 테이블 필드 목록을 새로 고치려면 Excel의 **옵션** 리본에서 **새로 고침**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a8c07-125">To refresh the PivotTable Field List, in Excel, on the **Options** ribbon, click **Refresh**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c07-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8c07-126">See Also</span></span>  
 [<span data-ttu-id="a8c07-127">Excel에서 분석&#40;SSAS 테이블 형식&#41;</span><span class="sxs-lookup"><span data-stu-id="a8c07-127">Analyze in Excel &#40;SSAS Tabular&#41;</span></span>](analyze-in-excel-ssas-tabular.md)  
  
  
