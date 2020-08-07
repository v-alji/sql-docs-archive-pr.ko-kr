---
title: 바로 가기 쿼리 파일을 전자 메일로 보내기(Excel용 MDS 추가 기능) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 5d46f20a-b04a-45c7-82af-02a2baaabbd7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c6474e6213ce67b31b0ea52eb548fab19562f438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731804"
---
# <a name="email-a-shortcut-query-file-mds-add-in-for-excel"></a><span data-ttu-id="7644c-102">바로 가기 쿼리 파일을 전자 메일로 보내기(Excel용 MDS 추가 기능)</span><span class="sxs-lookup"><span data-stu-id="7644c-102">Email a Shortcut Query File (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="7644c-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]에서는 사용자가 자신과 동일한 데이터를 사용 중인지 확인하려는 경우 해당 사용자에게 바로 가기 쿼리 파일을 메일로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], email a shortcut query file to someone when you want to ensure they're working with the same data that you are.</span></span> <span data-ttu-id="7644c-104">워크시트를 저장하고 전자 메일로 보내는 대신 쿼리를 공유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-104">You should share queries rather than saving the worksheet and emailing it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7644c-105">필수 조건</span><span class="sxs-lookup"><span data-stu-id="7644c-105">Prerequisites</span></span>  
 <span data-ttu-id="7644c-106">이 절차를 수행하려면</span><span class="sxs-lookup"><span data-stu-id="7644c-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7644c-107">Outlook 2010 이상이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-107">You must have Outlook 2010 or later installed.</span></span>  
  
-   <span data-ttu-id="7644c-108">Excel에서 활성 워크시트에 MDS 관리 데이터가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-108">You must have MDS-managed data in an active worksheet in Excel.</span></span>  
  
### <a name="to-send-a-shortcut-query-file"></a><span data-ttu-id="7644c-109">바로 가기 쿼리 파일을 보내려면</span><span class="sxs-lookup"><span data-stu-id="7644c-109">To send a shortcut query file</span></span>  
  
1.  <span data-ttu-id="7644c-110">워크시트의 데이터가 사용자가 공유하려는 형식인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-110">Ensure that the data in the worksheet is in the format you want to share.</span></span> <span data-ttu-id="7644c-111">데이터를 필터링 하 고 열을 다시 정렬 하는 방법에 대 한 자세한 내용은 [&#40;를 로드 하기 전에 데이터 필터링을 참조 Excel용 MDS 추가 기능&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) 하 고 [열 다시 정렬 &#40;Excel용 MDS 추가 기능&#41;](reorder-columns-mds-add-in-for-excel.md)</span><span class="sxs-lookup"><span data-stu-id="7644c-111">For more information about filtering data and reordering columns, see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) and [Reorder Columns &#40;MDS Add-in for Excel&#41;](reorder-columns-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="7644c-112">**저장 및 보내기** 그룹에서 **쿼리 보내기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-112">In the **Save and Send** group, click **Send Query**.</span></span> <span data-ttu-id="7644c-113">전자 메일 메시지가 열리고 바로 가기 쿼리 파일이 첨부됩니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-113">An email message opens and the shortcut query file is attached.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7644c-114">다음 단계</span><span class="sxs-lookup"><span data-stu-id="7644c-114">Next Steps</span></span>  
  
-   <span data-ttu-id="7644c-115">바로 가기 쿼리 파일을 열려면 전자 메일을 받는 사람이 MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] 을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-115">To open the shortcut query file, the recipient of the email must have the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] installed.</span></span> <span data-ttu-id="7644c-116">받는 사람이 파일을 두 번 클릭하여 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7644c-116">The recipient can double-click the file to open it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7644c-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7644c-117">See Also</span></span>  
 [<span data-ttu-id="7644c-118">바로 가기 쿼리 파일&#40;Excel용 MDS 추가 기능&#41;</span><span class="sxs-lookup"><span data-stu-id="7644c-118">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
  
