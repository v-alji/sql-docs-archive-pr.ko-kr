---
title: 고정 및 변경 특성 옵션(느린 변경 차원 마법사) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.attriboption.f1
ms.assetid: c841345c-7d03-452f-9379-1c8c464f029c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: df654cd97b343179828ebd94dea40eacc90e003d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87647773"
---
# <a name="fixed-and-changing-attribute-options-slowly-changing-dimension-wizard"></a><span data-ttu-id="6d5f4-102">고정 및 변경 특성 옵션(느린 변경 차원 마법사)</span><span class="sxs-lookup"><span data-stu-id="6d5f4-102">Fixed and Changing Attribute Options (Slowly Changing Dimension Wizard</span></span>
  <span data-ttu-id="6d5f4-103">**고정 및 변경 특성 옵션** 대화 상자를 사용하여 고정 및 변경 특성에서 변경 작업에 대응하는 방법을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5f4-103">Use the **Fixed and Changing Attribute Options** dialog box to specify how to respond to changes in fixed and changing attributes.</span></span>  
  
 <span data-ttu-id="6d5f4-104">이 마법사에 대한 자세한 내용은 [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="6d5f4-104">To learn more about this wizard, see [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="6d5f4-105">옵션</span><span class="sxs-lookup"><span data-stu-id="6d5f4-105">Options</span></span>  
 <span data-ttu-id="6d5f4-106">**고정 특성**</span><span class="sxs-lookup"><span data-stu-id="6d5f4-106">**Fixed attributes**</span></span>  
 <span data-ttu-id="6d5f4-107">고정 특성에서 변경이 감지된 경우 태스크를 실패한 것으로 처리할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d5f4-107">For fixed attributes, indicate whether the task should fail if a change is detected in a fixed attribute.</span></span>  
  
 <span data-ttu-id="6d5f4-108">**변경 특성**</span><span class="sxs-lookup"><span data-stu-id="6d5f4-108">**Changing attributes**</span></span>  
 <span data-ttu-id="6d5f4-109">변경 특성에서 변경이 감지된 경우 태스크 결과로 현재 레코드와 함께 오래된 레코드나 만료된 레코드를 변경할지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6d5f4-109">For changing attributes, indicate whether the task should change outdated or expired records, in addition to current records, when a change is detected in a changing attribute.</span></span> <span data-ttu-id="6d5f4-110">만료된 레코드란 유형 2 변경과 같이 기록 특성이 변경되어 새 레코드로 바뀐 레코드를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="6d5f4-110">An expired record is a record that has been replaced with a newer record by a change in a historical attribute (a Type 2 change).</span></span> <span data-ttu-id="6d5f4-111">이 옵션을 선택하면 관계형 데이터 웨어하우스에 생성된 다차원 개체의 추가 처리 요구 사항을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d5f4-111">Selecting this option may impose additional processing requirements on a multidimensional object constructed on the relational data warehouse.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d5f4-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6d5f4-112">See Also</span></span>  
 [<span data-ttu-id="6d5f4-113">느린 변경 차원 마법사를 사용하여 출력 구성</span><span class="sxs-lookup"><span data-stu-id="6d5f4-113">Configure Outputs Using the Slowly Changing Dimension Wizard</span></span>](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
