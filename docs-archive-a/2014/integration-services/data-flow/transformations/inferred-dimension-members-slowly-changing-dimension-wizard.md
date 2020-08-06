---
title: 유추 차원 멤버(느린 변경 차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.inferrdim.f1
ms.assetid: 809e395f-2e10-48ff-8860-56403f130628
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dda4345b91c69b134516baab2e5ba9b9990bd6af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659565"
---
# <a name="inferred-dimension-members-slowly-changing-dimension-wizard"></a><span data-ttu-id="ab1a2-102">유추 차원 멤버(느린 변경 차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="ab1a2-102">Inferred Dimension Members (Slowly Changing Dimension Wizard)</span></span>
  <span data-ttu-id="ab1a2-103">**유추 차원 멤버** 대화 상자를 사용하여 유추 멤버를 사용하기 위한 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-103">Use the **Inferred Dimension Members** dialog box to specify options for using inferred members.</span></span> <span data-ttu-id="ab1a2-104">유추 멤버는 팩트 테이블이 아직 로드되지 않은 차원 멤버를 참조할 때 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-104">Inferred members exist when a fact table references dimension members that are not yet loaded.</span></span> <span data-ttu-id="ab1a2-105">유추 멤버에 대한 데이터가 로드되면 새 레코드를 만드는 대신 기존 레코드를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-105">When data for the inferred member is loaded, you can update the existing record rather than create a new one.</span></span>  
  
 <span data-ttu-id="ab1a2-106">이 마법사에 대한 자세한 내용은 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-106">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="ab1a2-107">옵션</span><span class="sxs-lookup"><span data-stu-id="ab1a2-107">Options</span></span>  
 <span data-ttu-id="ab1a2-108">**유추 멤버 지원 사용**</span><span class="sxs-lookup"><span data-stu-id="ab1a2-108">**Enable inferred member support**</span></span>  
 <span data-ttu-id="ab1a2-109">유추 멤버를 사용하도록 선택한 경우 다음 두 옵션 중 하나를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-109">If you choose to enable inferred members, you must select one of the two options that follow.</span></span>  
  
 <span data-ttu-id="ab1a2-110">**변경 유형을 가진 열은 모두 Null임**</span><span class="sxs-lookup"><span data-stu-id="ab1a2-110">**All columns with a change type are null**</span></span>  
 <span data-ttu-id="ab1a2-111">새 유추 멤버 레코드에서 변경 유형을 가진 모든 열에 Null 값을 입력할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-111">Specify whether to enter null values in all columns with a change type in the new inferred member record.</span></span>  
  
 <span data-ttu-id="ab1a2-112">**부울 열을 사용하여 현재 레코드가 유추 멤버인지 여부 표시**</span><span class="sxs-lookup"><span data-stu-id="ab1a2-112">**Use a Boolean column to indicate whether the current record is an inferred member**</span></span>  
 <span data-ttu-id="ab1a2-113">기존 부울 열을 사용하여 현재 레코드가 유추 멤버인지 여부를 나타낼지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-113">Specify whether to use an existing Boolean column to indicate whether the current record is an inferred member.</span></span>  
  
 <span data-ttu-id="ab1a2-114">**유추 멤버 표시**</span><span class="sxs-lookup"><span data-stu-id="ab1a2-114">**Inferred member indicator**</span></span>  
 <span data-ttu-id="ab1a2-115">위에서 설명한 것처럼 부울 열을 사용하여 유추 멤버를 나타내도록 선택한 경우 목록에서 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ab1a2-115">If you have chosen to use a Boolean column to indicate inferred members as described above, select the column from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1a2-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab1a2-116">See Also</span></span>  
 [<span data-ttu-id="ab1a2-117">느린 변경 차원 마법사를 사용하여 출력 구성</span><span class="sxs-lookup"><span data-stu-id="ab1a2-117">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
