---
title: 테이블 속성 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- editTabProps
ms.assetid: 95ea72ba-8e40-4177-a963-0fb4d10c56e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1ba0809b99474704ec0e93e417a04d776bb26d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87648515"
---
# <a name="edit-the-table-properties"></a><span data-ttu-id="a8149-102">테이블 속성 편집</span><span class="sxs-lookup"><span data-stu-id="a8149-102">Edit the Table Properties</span></span>
  <span data-ttu-id="a8149-103">이 대화 상자를 사용하여 변경을 캡처 중인 선택된 테이블에서 특정 열을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-103">Use this dialog box to edit the specific columns from the selected table where changes are being captured.</span></span> <span data-ttu-id="a8149-104">또한 **보안 역할** 및 **캡처 인스턴스** 정보를 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-104">You can also edit the **Security Role** and **Capture Instance** information.</span></span>  
  
### <a name="to-edit-the-columns-to-include-in-the-cdc-instance"></a><span data-ttu-id="a8149-105">CDC 인스턴스에 포함할 열을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="a8149-105">To edit the columns to include in the CDC instance</span></span>  
  
1.  <span data-ttu-id="a8149-106">다음 중 하나 또는 모두를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-106">Do one or both of the following:</span></span>  
  
    -   <span data-ttu-id="a8149-107">포함할 추가 열의 옆에 있는 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-107">Select the check box next to any additional column you want to include.</span></span>  
  
    -   <span data-ttu-id="a8149-108">더 이상 포함하지 않을 열의 옆에 있는 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-108">Clear the check box next to any column that you no longer want to include.</span></span>  
  
### <a name="to-edit-the-security-role"></a><span data-ttu-id="a8149-109">보안 역할을 편집하려면</span><span class="sxs-lookup"><span data-stu-id="a8149-109">To edit the Security Role</span></span>  
  
1.  <span data-ttu-id="a8149-110">**보안 역할** 필드에서 새 이름을 입력하거나 보안 역할의 이름을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-110">Type a new name or edit the name of the security role in the **Security Role** field.</span></span>  
  
### <a name="to-create-a-new-capture-instance"></a><span data-ttu-id="a8149-111">새 캡처 인스턴스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="a8149-111">To create a new capture instance</span></span>  
  
1.  <span data-ttu-id="a8149-112">**보안 역할** 섹션의 **이름** 필드에 캡처 인스턴스의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-112">In the **Security Role** section, **Name** field enter a name for the capture instance.</span></span> <span data-ttu-id="a8149-113">기본적으로 이 필드에 입력된 이름의 끝에 **_NEW** 를 추가하면 현재 캡처 인스턴스의 이름이 됩니다(예: **old_instance_NEW**).</span><span class="sxs-lookup"><span data-stu-id="a8149-113">By default, the name entered in the field is the name of the current capture instance with **_NEW** added to the end of the name (for example, **old_instance_NEW**).</span></span>  
  
2.  <span data-ttu-id="a8149-114">캡처 인스턴스를 다음 중 하나로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-114">Save the capture instance as one of the following:</span></span>  
  
    -   <span data-ttu-id="a8149-115">**새 캡처 인스턴스**: 이 경우 새 캡처 인스턴스는 저장되지만, 이전 캡처 인스턴스는 삭제되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-115">**New Capture Instance**: In this case a new capture instance is saved and the old capture instance is not deleted.</span></span>  
  
         <span data-ttu-id="a8149-116">**참고**: 캡처 인스턴스는 테이블당 두 개를 초과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-116">**Note**: You can have no more than two capture instances per table.</span></span> <span data-ttu-id="a8149-117">이미 두 개의 캡처 인스턴스가 있는 경우에는 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-117">If there are already two capture instances, this option is not available.</span></span>  
  
    -   <span data-ttu-id="a8149-118">**기존 항목 바꾸기**: 이 경우 현재 캡처 인스턴스가 삭제되고 사용자가 만든 캡처 인스턴스로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-118">**Replace Existing**: In this case the current capture instance is deleted and replaced by the capture instance you created.</span></span> <span data-ttu-id="a8149-119">이 테이블에 대해 두 개의 캡처 인스턴스가 정의되어 있는 경우 하나를 선택하여 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-119">If there are two capture instances defined for this table, you must select one to replace.</span></span>  
  
 <span data-ttu-id="a8149-120">**참고**: **테이블** 탭의 테이블 목록에서 캡처 인스턴스를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-120">**Note**: You can remove a capture instance from the list of tables in the **Table** tab.</span></span>  
  
 <span data-ttu-id="a8149-121">이 대화 상자에 정보를 입력한 후 **확인** 을 클릭하여 변경 내용을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8149-121">After you finish entering the information in this dialog box, click **OK** to accept the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8149-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8149-122">See Also</span></span>  
 <span data-ttu-id="a8149-123">[CDC 인스턴스 속성을 편집하는 방법](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="a8149-123">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="a8149-124">변경 캡처를 위해 선택된 테이블 변경</span><span class="sxs-lookup"><span data-stu-id="a8149-124">Make Changes to the Tables Selected for Capturing Changes</span></span>](make-changes-to-the-tables-selected-for-capturing-changes.md)  
  
  
