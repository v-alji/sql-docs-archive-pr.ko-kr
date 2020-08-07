---
title: MDS 저장소에 연결(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c1db0594f07da7ff8a78642e4b2de0eb9e507164
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730795"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a><span data-ttu-id="927b1-102">MDS 저장소에 연결(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="927b1-102">Connect to an MDS Repository (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="927b1-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 데이터를 로드하거나 게시하기 전에 MDS 리포지토리에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], you must connect to an MDS repository before you can load or publish data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="927b1-104">필수 조건</span><span class="sxs-lookup"><span data-stu-id="927b1-104">Prerequisites</span></span>  
 <span data-ttu-id="927b1-105">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="927b1-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="927b1-106">**탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
### <a name="to-connect-to-an-mds-repository"></a><span data-ttu-id="927b1-107">MDS 저장소에 연결하려면</span><span class="sxs-lookup"><span data-stu-id="927b1-107">To connect to an MDS repository</span></span>  
  
1.  <span data-ttu-id="927b1-108">MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]의 **마스터 데이터** 탭에 있는 **연결 및 로드** 그룹에서 **연결** 단추 아래의 화살표를 클릭하고 **연결 관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-108">In the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], on the **Master Data** tab, in the **Connect and Load** group, click the arrow under the **Connect** button and click **Manage Connections**.</span></span>  
  
2.  <span data-ttu-id="927b1-109">**연결 관리** 대화 상자의 **새 연결** 섹션에서 **새 연결 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-109">On the **Manage Connections** dialog box, in the **New connection** section, click **Create a new connection**.</span></span>  
  
3.  <span data-ttu-id="927b1-110">**새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-110">Click **New**.</span></span>  
  
4.  <span data-ttu-id="927b1-111">**새 연결 추가** 대화 상자의 **설명** 필드에서 연결에 대한 설명을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-111">On the **Add New Connection** dialog box, in the **Description** field, type a description for your connection.</span></span> <span data-ttu-id="927b1-112">이 연결은 사용자가 도구 모음에서 **연결** 단추 아래의 화살표를 클릭할 때 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-112">This connection will be displayed when you click the arrow under the **Connect** button on the toolbar.</span></span>  
  
5.  <span data-ttu-id="927b1-113">**MDS 서버 주소** 상자에 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 웹 애플리케이션의 URL(예: http://contoso/mds)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-113">In the **MDS server address** box, type the URL of the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, for example http://contoso/mds.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="927b1-114">컴퓨터 이름을 사용해야 합니다. "localhost"는 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="927b1-114">Ensure that you use the computer name; do not use "localhost".</span></span>  
  
6.  <span data-ttu-id="927b1-115">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-115">Click **OK**.</span></span> <span data-ttu-id="927b1-116">이 이름은 **기존 연결** 섹션에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-116">The name is displayed in the **Existing Connections** section.</span></span>  
  
7.  <span data-ttu-id="927b1-117">선택적으로 **테스트** 를 클릭하여 연결을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-117">Optionally, click **Test** to test the connection.</span></span> <span data-ttu-id="927b1-118">확인 또는 오류 대화 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-118">A confirmation or error dialog is displayed.</span></span> <span data-ttu-id="927b1-119">**확인** 을 클릭하여 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-119">Click **OK** to close it.</span></span>  
  
8.  <span data-ttu-id="927b1-120">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-120">Click **Connect**.</span></span> <span data-ttu-id="927b1-121">**Master Data Services** 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="927b1-121">The **Master Data Services** pane is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="927b1-122">다음 단계</span><span class="sxs-lookup"><span data-stu-id="927b1-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="927b1-123">MDS에서 Excel로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="927b1-123">Load Data from MDS into Excel</span></span>](export-data-to-excel-from-master-data-services.md)  
  
-   [<span data-ttu-id="927b1-124">&#40;Excel용 MDS 추가 기능를 로드 하기 전에 데이터를 필터링&#41;</span><span class="sxs-lookup"><span data-stu-id="927b1-124">Filter Data before Loading &#40;MDS Add-in for Excel&#41;</span></span>](filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="927b1-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="927b1-125">See Also</span></span>  
 [<span data-ttu-id="927b1-126">연결&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="927b1-126">Connections &#40;MDS Add-in for Excel&#41;</span></span>](connections-mds-add-in-for-excel.md)  
  
  
