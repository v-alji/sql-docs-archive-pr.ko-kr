---
title: 데이터 계층 애플리케이션 삭제 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deletedacwizard.introduction.f1
- sql12.swb.deletedacwizard.deletedac.f1
- sql12.swb.deletedacwizard.summary.f1
- sql12.swb.deletedacwizard.choosemethod.f1
helpviewer_keywords:
- How to [DAC], delete
- data-tier application [SQL Server], delete
- wizard [DAC], delete
- delete DAC
ms.assetid: 16fe1c18-4486-424d-81d6-d276ed97482f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 602256c287a8c7bcf9d3fa5597b2fec2085c626c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736388"
---
# <a name="delete-a-data-tier-application"></a><span data-ttu-id="349ad-102">데이터 계층 애플리케이션 삭제</span><span class="sxs-lookup"><span data-stu-id="349ad-102">Delete a Data-tier Application</span></span>
  <span data-ttu-id="349ad-103">데이터 계층 애플리케이션 삭제 마법사 또는 Windows PowerShell 스크립트를 사용하여 데이터 계층 애플리케이션을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-103">You can delete a data-tier application by using either the Delete Data-tier Application wizard or a Windows PowerShell script.</span></span> <span data-ttu-id="349ad-104">연결된 데이터베이스를 보존, 분리 또는 삭제할지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-104">You can specify whether the associated database is retained, detached, or dropped.</span></span>  
  
-   <span data-ttu-id="349ad-105">**시작하기 전 주의 사항:**  [제한 사항](#LimitationsRestrictions), [사용 권한](#Permissions)</span><span class="sxs-lookup"><span data-stu-id="349ad-105">**Before you begin:**  [Limitations and Restrictions](#LimitationsRestrictions), [Permissions](#Permissions)</span></span>  
  
-   <span data-ttu-id="349ad-106">**DAC를 업그레이드하려면 다음을 사용합니다.**  [데이터 계층 애플리케이션 등록 마법사](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)</span><span class="sxs-lookup"><span data-stu-id="349ad-106">**To upgrade a DAC, using:**  [The Register Data-tier Application Wizard](#UsingDeleteDACWizard), [PowerShell](#DeleteDACPowerShell)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="349ad-107">시작하기 전에</span><span class="sxs-lookup"><span data-stu-id="349ad-107">Before You Begin</span></span>  
 <span data-ttu-id="349ad-108">DAC(데이터 계층 애플리케이션) 인스턴스를 삭제할 때는 데이터 계층 애플리케이션과 연결된 데이터베이스에 대해 어떠한 작업을 수행할지 지정하는 3가지 옵션 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-108">When you delete a data-tier application (DAC) instance, you choose one of three options specifying what is to be done with the database associated with the data-tier application.</span></span> <span data-ttu-id="349ad-109">3가지 옵션 모두 DAC 정의 메타데이터를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-109">All three options delete the DAC definition metadata.</span></span> <span data-ttu-id="349ad-110">각 옵션은 데이터 계층 애플리케이션과 연결된 데이터베이스에 대해 수행되는 작업에 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-110">The options differ in what they do with the database associated with the data-tier application.</span></span> <span data-ttu-id="349ad-111">마법사는 로그인처럼 DAC 또는 데이터베이스와 연결된 인스턴스 수준 개체는 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-111">The wizard does not delete any of the instance-level objects associated with the DAC or database, such as logins.</span></span>  
  
|<span data-ttu-id="349ad-112">옵션</span><span class="sxs-lookup"><span data-stu-id="349ad-112">Option</span></span>|<span data-ttu-id="349ad-113">데이터베이스 동작</span><span class="sxs-lookup"><span data-stu-id="349ad-113">Database actions</span></span>|  
|------------|----------------------|  
|<span data-ttu-id="349ad-114">등록 삭제</span><span class="sxs-lookup"><span data-stu-id="349ad-114">Delete registration</span></span>|<span data-ttu-id="349ad-115">연결된 데이터베이스가 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-115">The associated database remains intact.</span></span>|  
|<span data-ttu-id="349ad-116">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="349ad-116">Detach database</span></span>|<span data-ttu-id="349ad-117">연결된 데이터베이스가 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-117">The associated database is detached.</span></span> <span data-ttu-id="349ad-118">데이터베이스 엔진 인스턴스가 데이터베이스를 참조할 수는 없지만 데이터 및 로그 파일은 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-118">The instance of the Database Engine cannot reference the database, but the data and log files are intact.</span></span>|  
|<span data-ttu-id="349ad-119">데이터베이스 삭제</span><span class="sxs-lookup"><span data-stu-id="349ad-119">Delete database</span></span>|<span data-ttu-id="349ad-120">연결된 데이터베이스가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-120">The associated database is dropped.</span></span> <span data-ttu-id="349ad-121">데이터 및 로그 파일이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-121">The data and log files are deleted.</span></span>|  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> <span data-ttu-id="349ad-122">제한 사항</span><span class="sxs-lookup"><span data-stu-id="349ad-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="349ad-123">DAC를 삭제한 후 DAC 정의 메타데이터나 데이터베이스를 복원하는 자동 메커니즘은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-123">There is no automatic mechanism to restore the DAC definition metadata or the database after you delete a DAC.</span></span> <span data-ttu-id="349ad-124">DAC 인스턴스를 수동으로 다시 작성하는 방법은 삭제 옵션에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-124">How you can manually rebuild the DAC instance depends on the delete option.</span></span>  
  
|<span data-ttu-id="349ad-125">옵션</span><span class="sxs-lookup"><span data-stu-id="349ad-125">Option</span></span>|<span data-ttu-id="349ad-126">DAC 인스턴스를 다시 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="349ad-126">How to Rebuild the DAC Instance</span></span>|  
|------------|-------------------------------------|  
|<span data-ttu-id="349ad-127">등록 삭제</span><span class="sxs-lookup"><span data-stu-id="349ad-127">Delete registration</span></span>|<span data-ttu-id="349ad-128">남아 있는 데이터베이스에서 DAC를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-128">Register a DAC from the database left in place.</span></span>|  
|<span data-ttu-id="349ad-129">데이터베이스 분리</span><span class="sxs-lookup"><span data-stu-id="349ad-129">Detach database</span></span>|<span data-ttu-id="349ad-130">**sp_attachdb** 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 사용하여 데이터베이스를 다시 연결한 다음, 데이터베이스에 새 DAC 인스턴스를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-130">Re-attach the database by using **sp_attachdb** or [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then register a new DAC instance from the database.</span></span>|  
|<span data-ttu-id="349ad-131">데이터베이스 삭제</span><span class="sxs-lookup"><span data-stu-id="349ad-131">Delete database</span></span>|<span data-ttu-id="349ad-132">DAC가 삭제되기 전에 만든 전체 백업에서 데이터베이스를 복원한 다음, 데이터베이스에서 새 DAC 인스턴스를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-132">Restore the database from a full backup made before the DAC was deleted, and then register a new DAC instance from the database.</span></span>|  
  
> [!WARNING]  
>  <span data-ttu-id="349ad-133">복원하거나 다시 연결한 데이터베이스에서 DAC를 등록하여 DAC 인스턴스를 다시 작성하더라도 원래 DAC의 서버 선택 정책과 같은 일부 부분은 만들어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-133">Rebuilding a DAC instance by registering a DAC from a restored or re-attached database will not recreate some parts of the original DAC, such as the server selection policy.</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="349ad-134">권한</span><span class="sxs-lookup"><span data-stu-id="349ad-134">Permissions</span></span>  
 <span data-ttu-id="349ad-135">**sysadmin** 또는 **serveradmin** 고정 서버 역할의 멤버 또는 데이터베이스 소유자를 통해서만 DAC를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-135">A DAC can only be deleted by members of the **sysadmin** or **serveradmin** fixed server roles, or by the database owner.</span></span> <span data-ttu-id="349ad-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa **라는 기본 제공** 시스템 관리자 계정도 마법사를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-136">The built-in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator account named **sa** can also launch the wizard.</span></span>  
  
##  <a name="using-the-delete-data-tier-application-wizard"></a><a name="UsingDeleteDACWizard"></a> <span data-ttu-id="349ad-137">데이터 계층 애플리케이션 삭제 마법사 사용</span><span class="sxs-lookup"><span data-stu-id="349ad-137">Using the Delete Data-tier Application Wizard</span></span>  
 <span data-ttu-id="349ad-138">**마법사를 사용하여 DAC를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="349ad-138">**To Delete a DAC Using a Wizard**</span></span>  
  
1.  <span data-ttu-id="349ad-139">**개체 탐색기**에서 삭제할 DAC가 포함된 인스턴스에 대한 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-139">In **Object Explorer**, expand the node for the instance containing the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="349ad-140">**관리** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-140">Expand the **Management** node.</span></span>  
  
3.  <span data-ttu-id="349ad-141">**데이터 계층 애플리케이션** 노드를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-141">Expand the **Data-tier Applications** node.</span></span>  
  
4.  <span data-ttu-id="349ad-142">삭제할 DAC를 마우스 오른쪽 단추로 클릭한 다음, **데이터 계층 애플리케이션 삭제...** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-142">Right-click the DAC to be deleted, and then select **Delete Data-tier Application...**</span></span>  
  
5.  <span data-ttu-id="349ad-143">마법사 대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-143">Complete the wizard dialogs:</span></span>  
  
    1.  [<span data-ttu-id="349ad-144">소개</span><span class="sxs-lookup"><span data-stu-id="349ad-144">Introduction</span></span>](#Introduction)  
  
    2.  [<span data-ttu-id="349ad-145">방법 선택</span><span class="sxs-lookup"><span data-stu-id="349ad-145">Choose Method</span></span>](#Choose_method)  
  
    3.  [<span data-ttu-id="349ad-146">요약</span><span class="sxs-lookup"><span data-stu-id="349ad-146">Summary</span></span>](#Summary)  
  
    4.  [<span data-ttu-id="349ad-147">데이터 계층 애플리케이션 삭제</span><span class="sxs-lookup"><span data-stu-id="349ad-147">Delete Data-tier Application</span></span>](#Delete_datatier_application)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> <span data-ttu-id="349ad-148">소개 페이지</span><span class="sxs-lookup"><span data-stu-id="349ad-148">Introduction Page</span></span>  
 <span data-ttu-id="349ad-149">이 페이지에서는 데이터 계층 애플리케이션을 삭제하는 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-149">This page describes the steps for deleting a data-tier application.</span></span>  
  
 <span data-ttu-id="349ad-150">**이 페이지를 다시 표시 안 함**</span><span class="sxs-lookup"><span data-stu-id="349ad-150">**Do not show this page again.**</span></span> <span data-ttu-id="349ad-151">- 앞으로 이 페이지가 표시되지 않도록 하려면 이 확인란을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-151">- Click the check box to stop the page from being displayed in the future.</span></span>  
  
 <span data-ttu-id="349ad-152">**다음 >** - **방법 선택** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-152">**Next >** - Proceeds to the **Choose Method** page.</span></span>  
  
 <span data-ttu-id="349ad-153">**취소** - 데이터 계층 애플리케이션 또는 데이터베이스를 삭제하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-153">**Cancel** - Ends the wizard without deleting a data-tier application or database.</span></span>  
  
##  <a name="choose-method-page"></a><a name="Choose_method"></a> <span data-ttu-id="349ad-154">방법 선택 페이지</span><span class="sxs-lookup"><span data-stu-id="349ad-154">Choose Method Page</span></span>  
 <span data-ttu-id="349ad-155">이 페이지를 사용하여 삭제할 DAC와 연결된 데이터베이스를 처리하는 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-155">Use this page to specify the option for handling the database associated with the DAC to be deleted.</span></span>  
  
 <span data-ttu-id="349ad-156">**등록 삭제** - 데이터 계층 애플리케이션을 정의하는 메타데이터를 제거하되 연결된 데이터베이스는 그대로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-156">**Delete registration** - Removes the metadata defining the data-tier application, but leaves the associated database intact.</span></span>  
  
 <span data-ttu-id="349ad-157">**데이터베이스 분리** - 데이터 계층 애플리케이션을 정의하는 메타데이터를 제거하고 연결된 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-157">**Detach database** - Removes the metadata defining the data-tier application and detaches the associated database.</span></span>  
  
 <span data-ttu-id="349ad-158">[!INCLUDE[ssDE](../../includes/ssde-md.md)]의 해당 인스턴스는 더 이상 데이터베이스를 참조할 수 없지만 데이터 및 로그 파일은 그대로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-158">The database can no longer be referenced by that instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], but the data and log files remain intact.</span></span>  
  
 <span data-ttu-id="349ad-159">**데이터베이스 삭제** - DAC를 정의하는 메타데이터를 제거하고 연결된 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-159">**Delete database** - Removes the metadata defining the DAC and drops the associated database.</span></span>  
  
 <span data-ttu-id="349ad-160">데이터베이스에 대한 데이터 및 로그 파일이 영구적으로 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-160">The data and log files for the database are permanently deleted.</span></span>  
  
 <span data-ttu-id="349ad-161">\*\* \< 이전\*\* - **소개** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-161">**\< Previous** - Returns to the **Introduction** page.</span></span>  
  
 <span data-ttu-id="349ad-162">**다음 >** - **요약** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-162">**Next >** - Proceeds to the **Summary** page.</span></span>  
  
 <span data-ttu-id="349ad-163">**취소** - DAC 또는 데이터베이스를 삭제하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-163">**Cancel** - Ends the wizard without deleting the DAC or database.</span></span>  
  
##  <a name="summary-page"></a><a name="Summary"></a> <span data-ttu-id="349ad-164">요약 페이지</span><span class="sxs-lookup"><span data-stu-id="349ad-164">Summary Page</span></span>  
 <span data-ttu-id="349ad-165">이 페이지를 사용하여 DAC 인스턴스를 삭제할 때 마법사가 수행할 동작을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-165">Use this page to review the actions the wizard will take when deleting the DAC instance.</span></span>  
  
 <span data-ttu-id="349ad-166">**선택 항목 요약 검토** - 상자에 표시된 DAC, 데이터베이스 및 삭제 방법을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-166">**Review your selection summary** - Review the DAC, database, and deletion method displayed in the box.</span></span> <span data-ttu-id="349ad-167">정보가 올바르면 **다음** 또는 **마침** 을 선택하여 DAC를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-167">If the information is correct, select either **Next** or **Finish** to delete the DAC.</span></span> <span data-ttu-id="349ad-168">DAC 및 데이터베이스 정보가 올바르지 않으면 **취소** 를 선택하고 올바른 DAC를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-168">If the DAC and database information is not correct, select **Cancel** and select the correct DAC.</span></span> <span data-ttu-id="349ad-169">삭제 방법이 올바르지 않으면 **이전** 을 선택하여 **방법 선택** 페이지로 돌아간 후 다른 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-169">If the deletion method is not correct, select **Previous** to return to the **Choose Method** page and select a different method.</span></span>  
  
 <span data-ttu-id="349ad-170">\*\* \< 이전\*\* -다른 삭제 방법을 선택할 수 있도록 **방법 선택** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-170">**\< Previous** - Returns to the **Choose Method** page to choose a different delete method.</span></span>  
  
 <span data-ttu-id="349ad-171">**다음 &gt;** - 이전 페이지에서 선택한 방법을 사용하여 DAC 인스턴스를 삭제하고 **데이터 계층 애플리케이션 삭제** 페이지로 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-171">**Next >** - Deletes the DAC instance using the method you chose on the previous page, and proceeds to the **Delete Data-tier Application** page.</span></span>  
  
 <span data-ttu-id="349ad-172">**취소** - DAC 인스턴스를 삭제하지 않고 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-172">**Cancel** - Ends the wizard without deleting the DAC instance.</span></span>  
  
##  <a name="delete-data-tier-application-page"></a><a name="Delete_datatier_application"></a><span data-ttu-id="349ad-173">데이터 계층 응용 프로그램 삭제 페이지</span><span class="sxs-lookup"><span data-stu-id="349ad-173">Delete Data-tier Application Page</span></span>  
 <span data-ttu-id="349ad-174">이 페이지에서는 삭제 작업의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-174">This page reports the success or failure of the delete operation.</span></span>  
  
 <span data-ttu-id="349ad-175">**DAC 삭제** - DAC 인스턴스를 삭제하기 위해 수행한 각 동작의 성공 또는 실패를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-175">**Deleting the DAC** - Reports the success or failure of each action taken to delete the DAC instance.</span></span> <span data-ttu-id="349ad-176">정보를 검토하여 각 동작의 성공 또는 실패를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-176">Review the information to determine the success or failure of each action.</span></span> <span data-ttu-id="349ad-177">오류가 발생한 동작에는 모두 **결과** 열에 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-177">Any action that encountered an error will have a link in the **Result** column.</span></span> <span data-ttu-id="349ad-178">링크를 선택하면 해당 동작의 오류에 대한 보고서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-178">Select the link to view a report of the error for that action.</span></span>  
  
 <span data-ttu-id="349ad-179">**보고서 저장** - 삭제 보고서를 HTML 파일로 저장하려면 이 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-179">**Save Report** - Select this button to save the deletion report to an HTML file.</span></span> <span data-ttu-id="349ad-180">파일은 모든 동작에서 생성된 모든 오류를 비롯하여 각 동작의 상태를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-180">The file reports the status of each action, including all errors generated by any of the actions.</span></span> <span data-ttu-id="349ad-181">기본 폴더는 Windows 계정의 Documents 폴더에 있는 SQL Server Management Studio\DAC Packages 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-181">The default folder is a SQL Server Management Studio\DAC Packages folder in the Documents folder of your Windows account..</span></span>  
  
 <span data-ttu-id="349ad-182">**마침** - 마법사를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-182">**Finish** - Ends the wizard.</span></span>  
  
##  <a name="delete-a-dac-using-powershell"></a><a name="DeleteDACPowerShell"></a><span data-ttu-id="349ad-183">PowerShell을 사용 하 여 DAC 삭제</span><span class="sxs-lookup"><span data-stu-id="349ad-183">Delete a DAC Using PowerShell</span></span>  
 <span data-ttu-id="349ad-184">**PowerShell 스크립트를 사용하여 DAC를 삭제하려면**</span><span class="sxs-lookup"><span data-stu-id="349ad-184">**To delete a DAC using a PowerShell script**</span></span>  
  
1.  <span data-ttu-id="349ad-185">SMO Server 개체를 만든 다음 삭제할 DAC를 포함하는 인스턴스로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-185">Create a SMO Server object and set it to the instance that contains the DAC to be deleted.</span></span>  
  
2.  <span data-ttu-id="349ad-186">`ServerConnection` 개체를 열고 동일한 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-186">Open a `ServerConnection` object and connect to the same instance.</span></span>  
  
3.  <span data-ttu-id="349ad-187">`add_DacActionStarted` 및 `add_DacActionFinished`를 사용하여 DAC 업그레이드 이벤트에 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-187">Use `add_DacActionStarted` and `add_DacActionFinished` to subscribe to the DAC upgrade events.</span></span>  
  
4.  <span data-ttu-id="349ad-188">삭제할 DAC를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-188">Specify the DAC to delete.</span></span>  
  
5.  <span data-ttu-id="349ad-189">적합한 삭제 옵션에 따라 다음 세 개의 코드 중 하나를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-189">Use one of these three sets of code, depending on which delete option is appropriate:</span></span>  
  
    -   <span data-ttu-id="349ad-190">DAC 등록만 삭제하고 데이터베이스를 그대로 두려면 `Unmanage()` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-190">To delete the DAC registration but leave the database intact, use the `Unmanage()` method.</span></span>  
  
    -   <span data-ttu-id="349ad-191">DAC 등록을 삭제하고 데이터베이스를 분리하려면 `Uninstall()` 메서드를 사용하고 `DetachDatabase`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-191">To delete the DAC registration and detach the database, use the `Uninstall()` method and specify `DetachDatabase`.</span></span>  
  
    -   <span data-ttu-id="349ad-192">DAC 등록을 삭제하고 데이터베이스를 삭제하려면 `Uninstall()` 메서드를 사용하고 `DropDatabase`를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-192">To delete the DAC registration and drop the database, use the `Uninstall()` method and specify `DropDatabase`.</span></span>  
  
### <a name="example-deleting-the-dac-but-leaving-the-database-powershell"></a><span data-ttu-id="349ad-193">DAC를 삭제하지만 데이터베이스를 그대로 두는 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="349ad-193">Example Deleting the DAC but Leaving the Database (PowerShell)</span></span>  
 <span data-ttu-id="349ad-194">다음 예에서는 `Unmanage()` 메서드를 사용하여 MyApplication이라는 DAC는 삭제하고 데이터베이스는 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-194">The following example deletes a DAC named MyApplication using the `Unmanage()` method to delete the DAC but leave the database intact.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Only delete the DAC definition from msdb, the associated database remains active.  
$dacstore.Unmanage($dacName)  
```  
  
### <a name="example-deleting-the-dac-and-detaching-the-database-powershell"></a><span data-ttu-id="349ad-195">DAC를 삭제하지만 데이터베이스를 분리하는 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="349ad-195">Example Deleting the DAC and Detaching the Database (PowerShell)</span></span>  
 <span data-ttu-id="349ad-196">다음 예에서는 `Uninstall()` 메서드를 사용하여 MyApplication이라는 DAC를 삭제하고 데이터베이스를 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-196">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and detach the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = get-item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and detach the associated database.  
$dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DetachDatabase)  
```  
  
### <a name="example-deleting-the-dac-and-dropping-the-database-powershell"></a><span data-ttu-id="349ad-197">DAC를 삭제하고 데이터베이스를 삭제하는 예(PowerShell)</span><span class="sxs-lookup"><span data-stu-id="349ad-197">Example Deleting the DAC and Dropping the Database (PowerShell)</span></span>  
 <span data-ttu-id="349ad-198">다음 예에서는 `Uninstall()` 메서드를 사용하여 MyApplication이라는 DAC를 삭제하고 데이터베이스를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="349ad-198">The following example deletes a DAC named MyApplication using the `Uninstall()` method to delete the DAC and drop the database.</span></span>  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Open a Common.ServerConnection to the same instance.  
$serverconnection = New-Object Microsoft.SqlServer.Management.Common.ServerConnection($srv.ConnectionContext.SqlConnectionObject)  
$serverconnection.Connect()  
$dacstore = New-Object Microsoft.SqlServer.Management.Dac.DacStore($serverconnection)  
  
## Subscribe to the DAC delete events.  
$dacstore.add_DacActionStarted({Write-Host `n`nStarting at $(get-date) :: $_.Description})  
$dacstore.add_DacActionFinished({Write-Host Completed at $(get-date) :: $_.Description})  
  
## Specify the DAC to delete.  
$dacName  = "MyApplication"  
  
## Delete the DAC definition from msdb and drop the associated database.  
## $dacstore.Uninstall($dacName, [Microsoft.SqlServer.Management.Dac.DacUninstallMode]::DropDatabase)  
```  
  
## <a name="see-also"></a><span data-ttu-id="349ad-199">참고 항목</span><span class="sxs-lookup"><span data-stu-id="349ad-199">See Also</span></span>  
 <span data-ttu-id="349ad-200">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="349ad-200">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="349ad-201">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="349ad-201">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="349ad-202">[데이터 계층 응용 프로그램 배포](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="349ad-202">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 <span data-ttu-id="349ad-203">[DAC로 데이터베이스 등록](register-a-database-as-a-dac.md) </span><span class="sxs-lookup"><span data-stu-id="349ad-203">[Register a Database As a DAC](register-a-database-as-a-dac.md) </span></span>  
 <span data-ttu-id="349ad-204">[SQL Server 데이터베이스 백업 및 복원](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="349ad-204">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="349ad-205">데이터베이스 분리 및 연결&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="349ad-205">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
