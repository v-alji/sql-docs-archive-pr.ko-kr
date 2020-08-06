---
title: 모델 항목 보안 페이지 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.modelproperties.modelitemsecurity.f1
ms.assetid: 8c5b29ae-1f17-41f2-ab59-97899b8fb4fc
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 928572437990c7f7fe1117c086c65c939aa9c999
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639391"
---
# <a name="model-item-security-page-report-manager"></a><span data-ttu-id="329b8-102">모델 항목 보안 페이지(보고서 관리자)</span><span class="sxs-lookup"><span data-stu-id="329b8-102">Model Item Security Page (Report Manager)</span></span>
  <span data-ttu-id="329b8-103">이 페이지를 사용하여 특정 항목에 대한 읽기 전용 권한을 부여 또는 취소하는 방법으로 모델의 부분에 보안을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-103">Use this page to secure parts of a model by granting or revoking read-only permissions on particular items.</span></span> <span data-ttu-id="329b8-104">모델 항목 보안은 런타임에 임시 데이터 탐색에 영향을 미치며 보고서 작성기에서 보고서를 만들 때 게시된 모델의 부분을 사용하는 기능에도 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-104">Model item security affects ad hoc data exploration at run time and the ability to use parts of a published model when creating reports in Report Builder.</span></span> <span data-ttu-id="329b8-105">이 기능을 사용하려면 내용 관리자 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-105">To use this feature, you must have Content Manager permissions.</span></span>  
  
 <span data-ttu-id="329b8-106">모델 항목 보안은 보고서 서버에서 처리되는 모델에 적용되며 모델 디자이너에서 편집하거나 보고서 디자이너에서 사용하는 .smdl 파일에는 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-106">Model item security is applied to a model that is processed on the report server and does not affect .smdl files that you edit in Model Designer or use in Report Designer.</span></span> <span data-ttu-id="329b8-107">또한 모델 정의를 수정할 수 있는 권한을 가진 사용자에게도 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-107">Furthermore, it has no effect on users who have permission to modify a model definition.</span></span> <span data-ttu-id="329b8-108">모델에 대한 내용 관리자 또는 게시자 권한을 가진 사용자는 모델 항목 보안의 적용 여부에 관계없이 모델의 모든 부분을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-108">Any user who has Content Manager or Publisher permissions on a model can see all parts of it, regardless of whether you apply model item security.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="329b8-109">모델 항목 보안은 보안 필터를 통해 더 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-109">Model items can be further secured through the use of security filters.</span></span>  
  
 <span data-ttu-id="329b8-110">모델 내의 엔터티, 폴더 및 개별 필드에서 모델 항목 보안을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-110">You can define model item security on entities, folders, and individual fields within a model.</span></span> <span data-ttu-id="329b8-111">모델은 넓은 영역의 보안 가능한 항목을 제시하기 때문에 비교적 적은 수의 역할 할당을 통해 많은 수의 항목에 보안을 설정할 수 있도록 사용 권한 상속이 모델에 기본 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-111">Because a model presents such a large surface of securable items, permission inheritance is built into the model so that you can secure a large number of items through a relatively small number of role assignments.</span></span> <span data-ttu-id="329b8-112">사용 권한 상속은 다음을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-112">Permission inheritance is based on the following:</span></span>  
  
-   <span data-ttu-id="329b8-113">모델</span><span class="sxs-lookup"><span data-stu-id="329b8-113">Model</span></span>  
  
-   <span data-ttu-id="329b8-114">루트 노드</span><span class="sxs-lookup"><span data-stu-id="329b8-114">Root node</span></span>  
  
-   <span data-ttu-id="329b8-115">폴더 또는 엔터티</span><span class="sxs-lookup"><span data-stu-id="329b8-115">Folders or entities</span></span>  
  
-   <span data-ttu-id="329b8-116">필드</span><span class="sxs-lookup"><span data-stu-id="329b8-116">Fields</span></span>  
  
 <span data-ttu-id="329b8-117">처음에는 모델 항목에 대한 액세스 권한은 모델 자체에 설정된 역할 할당을 통해 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-117">Initially, permission to access to model items is inherited through role assignments that are set on the model itself.</span></span> <span data-ttu-id="329b8-118">보고서 관리자의 폴더에 있는 모델을 볼 권한이 있는 사용자는 모델의 모든 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-118">A user who has permission to view a model in a folder in Report Manager can view all of the items in the model.</span></span>  
  
 <span data-ttu-id="329b8-119">모델 항목 보안을 적용하는 경우 루트 노드에 하나 이상의 역할 할당을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-119">If you apply model item security, you must create at least one role assignment on the root node.</span></span> <span data-ttu-id="329b8-120">루트 노드에 대한 이 최초 역할 할당은 상속되는 사용 권한의 새로운 원본 역할을 하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-120">This initial role assignment on the root node becomes the new source of inherited permissions.</span></span> <span data-ttu-id="329b8-121">루트 노드의 역할 할당은 모델 계층의 모든 항목에 의해 자동으로 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-121">The role assignment on the root node is automatically inherited by all items in the model hierarchy.</span></span>  
  
 <span data-ttu-id="329b8-122">데이터 탐색에 대한 사용 권한을 추가로 사용자 지정하려면 폴더와 엔터티에 대한 사용 권한을 변경하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-122">To further customize permissions on data exploration, you can vary permissions on folders and entities.</span></span> <span data-ttu-id="329b8-123">마지막으로, 개별 필드에 대한 사용 권한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-123">Finally, you can set permissions on individual fields.</span></span>  
  
 <span data-ttu-id="329b8-124">역할 할당을 유지 관리하기 쉽도록 만들려면 개별 필드 대신 폴더 또는 엔터티에만 사용 권한을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-124">To make role assignments easier to maintain, set permissions only on folders or entities rather than individual fields.</span></span> <span data-ttu-id="329b8-125">만든 역할 할당은 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-125">You cannot search for role assignments that you create.</span></span> <span data-ttu-id="329b8-126">특정 필드에 대해 보안을 설정하고 나중에 이 보안 설정을 업데이트하려면 모델 네임스페이스를 하나씩 클릭하여 보안을 설정한 필드를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-126">If you set security on specific fields and you want to update the security settings later, you must click through the model namespace to find the fields you secured.</span></span>  
  
 <span data-ttu-id="329b8-127">시작하려면 루트 노드에서 역할 할당을 만든 다음 엔터티와 폴더에서 추가 역할 할당을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-127">To get started, create a role assignment on the root node and then create additional role assignments on entities and folders.</span></span> <span data-ttu-id="329b8-128">모델 항목 보안을 취소하려면 **개별 모델 항목을 이 모델에 대해 독립적으로 유지**확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-128">To clear model item security, clear the check box for **Secure individual model items independently for this model**.</span></span> <span data-ttu-id="329b8-129">확인란의 선택을 취소하면 모델에서 상속된 최초 사용 권한으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-129">Clearing the check box reverts back to the initial permissions that are inherited from the model.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="329b8-130">탐색</span><span class="sxs-lookup"><span data-stu-id="329b8-130">Navigation</span></span>  
 <span data-ttu-id="329b8-131">사용자 인터페이스(UI)에서 이 위치를 탐색하려면 다음 절차를 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="329b8-131">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-general-properties-page-for-a-report"></a><span data-ttu-id="329b8-132">보고서의 일반 속성 페이지를 열려면</span><span class="sxs-lookup"><span data-stu-id="329b8-132">To open the General properties page for a report</span></span>  
  
1.  <span data-ttu-id="329b8-133">보고서 관리자를 열고 모델 항목의 보안을 구성할 모델을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-133">Open Report Manager, and locate the model for which you want to configure security for model items.</span></span>  
  
2.  <span data-ttu-id="329b8-134">모델 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-134">Hover over the model, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="329b8-135">드롭다운 메뉴에서 **관리**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-135">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="329b8-136">모델의 일반 속성 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-136">This opens the General properties page for the model.</span></span>  
  
4.  <span data-ttu-id="329b8-137">**모델 항목 보안** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-137">Select the **Model Item Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="329b8-138">옵션</span><span class="sxs-lookup"><span data-stu-id="329b8-138">Options</span></span>  
 <span data-ttu-id="329b8-139">**개별 모델 항목을 이 모델에 대해 독립적으로 유지**</span><span class="sxs-lookup"><span data-stu-id="329b8-139">**Secure individual model items independently for this model**</span></span>  
 <span data-ttu-id="329b8-140">모델 항목 보안을 사용하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-140">Click this check box to enable model item security.</span></span>  
  
 <span data-ttu-id="329b8-141">**모델의 개별 모델 항목에 대한 보안 지정**</span><span class="sxs-lookup"><span data-stu-id="329b8-141">**Specify security for individual model items in the mode**</span></span>  
 <span data-ttu-id="329b8-142">모델의 모든 항목을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-142">Shows all of the items in a model.</span></span> <span data-ttu-id="329b8-143">모델 네임스페이스를 탐색하여 보안을 설정하려는 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-143">You can navigate the model namespace to select the item you want to secure.</span></span> <span data-ttu-id="329b8-144">한 번에 한 항목만 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-144">You can only select one item at a time.</span></span> <span data-ttu-id="329b8-145">다른 엔터티 및 폴더로 진행하기 전에 루트 노드에서 첫 역할 할당을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-145">Be sure to create the first role assignment on the root node before proceeding to other entities and folders.</span></span>  
  
 <span data-ttu-id="329b8-146">**부모 항목으로부터 권한 상속**</span><span class="sxs-lookup"><span data-stu-id="329b8-146">**Inherit permissions from the parent item**</span></span>  
 <span data-ttu-id="329b8-147">부모 항목의 보안 설정을 상속하려면 이 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-147">Click this option to inherit the security settings of the parent item.</span></span>  
  
 <span data-ttu-id="329b8-148">**다음 사용자 및 그룹(세미콜론으로 구분)에 읽기 권한 할당**</span><span class="sxs-lookup"><span data-stu-id="329b8-148">**Assign read permission to the following users and groups (semi-colon separated)**</span></span>  
 <span data-ttu-id="329b8-149">액세스 권한을 정의할 사용자 또는 그룹 계정을 지정하려면 이 옵션을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-149">Click this option to specify the user or group account for which you are defining access.</span></span> <span data-ttu-id="329b8-150">기본 보안을 사용하는 경우 사용자 및 그룹 계정은 Windows 도메인 계정입니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-150">If you are using default security, the user and group accounts are Windows domain accounts.</span></span> <span data-ttu-id="329b8-151">계정을 \* \<domain> \\<계정 \> \*형식으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="329b8-151">Specify the accounts in this format: *\<domain>\\<account\>*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329b8-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="329b8-152">See Also</span></span>  
 [<span data-ttu-id="329b8-153">Management Studio의 보고서 서버 F1 도움말</span><span class="sxs-lookup"><span data-stu-id="329b8-153">Report Server in Management Studio F1 Help</span></span>](tools/report-server-in-management-studio-f1-help.md)  
  
  
