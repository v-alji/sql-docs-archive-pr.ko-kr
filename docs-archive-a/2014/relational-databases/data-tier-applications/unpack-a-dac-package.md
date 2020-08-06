---
title: DAC 패키지 압축 풀기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- wizard [DAC], unpack
- data-tier application [SQL Server], unpack
- How to [DAC], unpack
- unpack DAC
ms.assetid: 697b69b3-f157-4e22-ac4e-f65c5fc2d0ad
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5ba0930f79a47696a6c9a9c1bfe028316601f64b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661144"
---
# <a name="unpack-a-dac-package"></a><span data-ttu-id="f887d-102">DAC 패키지 압축 풀기</span><span class="sxs-lookup"><span data-stu-id="f887d-102">Unpack a DAC Package</span></span>
  <span data-ttu-id="f887d-103">데이터 계층 애플리케이션 압축 풀기 대화 상자를 사용하여 DAC(데이터 계층 애플리케이션) 패키지에서 스크립트와 파일 압축을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-103">Use the Unpack Data-tier Application dialog box to unzip the scripts and files from a data-tier application (DAC) package.</span></span> <span data-ttu-id="f887d-104">스크립트와 파일은 폴더에 저장되며 패키지를 사용하여 DAC를 프로덕션 시스템에 배포하기 전에 폴더에서 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-104">The scripts and files are placed in a folder where they can be reviewed before the package is used to deploy the DAC into a production system.</span></span> <span data-ttu-id="f887d-105">한 DAC의 내용을 다른 폴더에 압축을 푼 다른 패키지의 내용과 비교할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-105">The contents of one DAC can also be compared with the contents of another package unpacked to another folder.</span></span>  
  
1.  <span data-ttu-id="f887d-106">**시작하기 전 주의 사항:**  [보안](#Security)</span><span class="sxs-lookup"><span data-stu-id="f887d-106">**Before you begin:**  [Security](#Security)</span></span>  
  
2.  <span data-ttu-id="f887d-107">**DAC의 압축을 풀려면 다음을 사용합니다.**  [데이터 계층 애플리케이션 압축 풀기 대화 상자](#UnpackDACDial), [DAC 패키지의 내용 검사](#ExamDACPack)</span><span class="sxs-lookup"><span data-stu-id="f887d-107">**To unpack a DAC, using:**  [Unpack Data-tier Application Dialog](#UnpackDACDial), [Examine the Contents of a DAC Package](#ExamDACPack)</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f887d-108">보안</span><span class="sxs-lookup"><span data-stu-id="f887d-108">Security</span></span>  
 <span data-ttu-id="f887d-109">출처를 알 수 없거나 신뢰할 수 없는 DAC 패키지는 배포하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-109">We recommend that you do not deploy a DAC package from unknown or untrusted sources.</span></span> <span data-ttu-id="f887d-110">이러한 DAC에 포함된 악성 코드가 의도하지 않은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 코드를 실행하거나 스키마를 수정하여 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-110">Such DACs could contain malicious code that might execute unintended [!INCLUDE[tsql](../../includes/tsql-md.md)] code or cause errors by modifying the schema.</span></span> <span data-ttu-id="f887d-111">출처를 알 수 없거나 신뢰할 수 없는 DAC를 사용하려면 먼저 격리된 테스트 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 배포하고 DAC 압축을 푼 다음 저장 프로시저나 다른 사용자 정의 코드와 같은 코드를 검사하십시오.</span><span class="sxs-lookup"><span data-stu-id="f887d-111">Before you use a DAC from an unknown or untrusted source, deploy it on an isolated test instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], unpack the DAC and examine the code, such as stored procedures or other user-defined code.</span></span>  
  
##  <a name="unpack-data-tier-application-dialog"></a><a name="UnpackDACDial"></a> <span data-ttu-id="f887d-112">데이터 계층 애플리케이션 압축 풀기 대화 상자</span><span class="sxs-lookup"><span data-stu-id="f887d-112">Unpack Data-tier Application Dialog</span></span>  
 <span data-ttu-id="f887d-113">**DAC 패키지 파일을 압축을 풀려면**</span><span class="sxs-lookup"><span data-stu-id="f887d-113">**To Unpack a DAC Package File**</span></span>  
  
-   <span data-ttu-id="f887d-114">**Windows 탐색기**에서 DAC 패키지(.dacpac) 파일의 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-114">In **Windows Explorer**, navigate to the location of a DAC package (.dacpac) file.</span></span>  
  
-   <span data-ttu-id="f887d-115">다음 두 가지 방법 중 하나를 사용하여 데이터 계층 애플리케이션 압축 풀기 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-115">Use one of these two methods to open the Unpack Data-tier Application dialog:</span></span>  
  
    1.  <span data-ttu-id="f887d-116">DAC 패키지(.dacpac) 파일을 마우스 오른쪽 단추로 클릭하고 **압축 풀기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-116">Right-click the DAC package (.dacpac) file and select **Unpack**.</span></span>  
  
    2.  <span data-ttu-id="f887d-117">DAC 패키지 파일을 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-117">Double-click the DAC package file.</span></span>  
  
-   <span data-ttu-id="f887d-118">대화 상자를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-118">Complete the dialogs:</span></span>  
  
    -   [<span data-ttu-id="f887d-119">Microsoft SQL Server DAC 패키지 파일 압축 풀기</span><span class="sxs-lookup"><span data-stu-id="f887d-119">Unpack Microsoft SQL Server DAC Package File</span></span>](#Unpack)  
  
    -   [<span data-ttu-id="f887d-120">폴더 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f887d-120">Browse for Folder</span></span>](#Browse)  
  
###  <a name="unpack-microsoft-sql-server-dac-package-file"></a><a name="Unpack"></a> <span data-ttu-id="f887d-121">Microsoft SQL Server DAC 패키지 파일 압축 풀기</span><span class="sxs-lookup"><span data-stu-id="f887d-121">Unpack Microsoft SQL Server DAC Package File</span></span>  
 <span data-ttu-id="f887d-122">이 페이지를 사용하여 파일 압축을 풀 대상 폴더를 지정하고 압축 풀기 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-122">Use this page to specify the destination folder in which to place the unpacked files, and then run the unpack operation.</span></span>  
  
 <span data-ttu-id="f887d-123">**다음 폴더에 파일 압축 풀기:** - 파일 압축을 풀 폴더의 전체 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-123">**Files will be unpacked to this folder:** - Specify the full path to the folder for the unpacked files.</span></span> <span data-ttu-id="f887d-124">폴더가 존재하고 전체 경로를 아는 경우 입력란에 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-124">If the folder exists and you know the full path, type the path in the box.</span></span> <span data-ttu-id="f887d-125">그렇지 않으면 **찾아보기** 단추를 클릭하여 폴더로 이동하거나 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-125">If not, click the **Browse** button to navigate to a folder or create a new folder.</span></span>  
  
 <span data-ttu-id="f887d-126">**찾아보기** - 파일 계층을 탐색하거나 새 폴더를 만들어 폴더를 선택할 수 있는 **폴더 찾아보기** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-126">**Browse** - Opens the **Browse for Folder** page where you can choose a folder by navigating the file hierarchy, or create a new folder.</span></span>  
  
 <span data-ttu-id="f887d-127">**압축 풀기** - 압축 풀기 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-127">**Unpack** - Starts the unpack operation.</span></span>  
  
 <span data-ttu-id="f887d-128">**취소** - DAC 패키지 압축을 풀지 않고 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-128">**Cancel** - Terminates the dialog box without unpacking the DAC package.</span></span>  
  
###  <a name="browse-for-folder"></a><a name="Browse"></a> <span data-ttu-id="f887d-129">폴더 찾아보기</span><span class="sxs-lookup"><span data-stu-id="f887d-129">Browse for Folder</span></span>  
 <span data-ttu-id="f887d-130">이 페이지를 사용하여 압축 풀기 작업의 대상 폴더를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-130">Use this page to choose the destination folder for the unpack operation.</span></span> <span data-ttu-id="f887d-131">필요에 따라 새 폴더를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-131">Optionally, you can also create a new folder.</span></span>  
  
 <span data-ttu-id="f887d-132">**폴더 목록** - 컴퓨터의 파일 계층을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-132">**Folder list** - Displays the file hierarchy for your computer.</span></span> <span data-ttu-id="f887d-133">노드를 확장하여 DAC 패키지 압축을 풀 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-133">Expand the nodes to navigate to the folder in which to unpack the DAC package.</span></span> <span data-ttu-id="f887d-134">폴더를 클릭한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-134">Click on the folder and then click **OK**.</span></span>  
  
 <span data-ttu-id="f887d-135">**새 폴더 만들기** - 폴더 계층에서 현재 선택된 폴더에 생성될 새 폴더의 이름을 지정할 수 있는 대화 상자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-135">**Make New Folder** - Opens a dialog in which you can specify the name for a new folder to be created in the folder you have currently selected in the folder hierarchy.</span></span>  
  
 <span data-ttu-id="f887d-136">**확인** - **DAC 패키지 파일 압축 풀기** 페이지의 **다음 폴더에 파일 압축 풀기** 입력란에 선택되어 있는 폴더에 대한 경로를 적용하고 해당 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-136">**OK** - Places the path to the folder you selected in the **Files will be unpacked to this folder** box of the **Unpack DAC Package File** page and returns you to that page.</span></span>  
  
 <span data-ttu-id="f887d-137">**취소** - 폴더를 선택하지 않고 대화 상자를 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-137">**Cancel** - Terminates the dialog box without selecting a folder.</span></span>  
  
##  <a name="examine-the-contents-of-a-dac-package"></a><a name="ExamDACPack"></a> <span data-ttu-id="f887d-138">DAC 패키지의 내용 검사</span><span class="sxs-lookup"><span data-stu-id="f887d-138">Examine the Contents of a DAC Package</span></span>  
 <span data-ttu-id="f887d-139">패키지의 압축을 푼 후에는 **데이터 계층 애플리케이션 압축 풀기** 대화 상자에서 생성한 파일을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-139">After unpacking the package, you can examine the files produced by the **Unpack Data-tier Application** dialog.</span></span> <span data-ttu-id="f887d-140">대화 상자는 선택된 대상 폴더에 다음 파일을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-140">The dialog box builds the following files in the selected destination folder:</span></span>  
  
1.  <span data-ttu-id="f887d-141">DAC에 정의된 개체를 생성하는 문을 포함하는 Transact-SQL 스크립트.</span><span class="sxs-lookup"><span data-stu-id="f887d-141">A Transact-SQL script that contains the statements for creating the objects defined in the DAC.</span></span> <span data-ttu-id="f887d-142">파일 이름은 *DACName*.sql이며 *DACName* 은 DAC의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f887d-142">The file name is *DACName*.sql, where *DACName* is the name of the DAC.</span></span>  
  
2.  <span data-ttu-id="f887d-143">패키지의 모든 XML 파일</span><span class="sxs-lookup"><span data-stu-id="f887d-143">All XML files from the package.</span></span>  
  
3.  <span data-ttu-id="f887d-144">DAC 배포 전 또는 배포 후 파일과 같은 DAC의 여분 파일에 있는 모든 파일</span><span class="sxs-lookup"><span data-stu-id="f887d-144">All files from the Extra Files section of the DAC, such as the DAC pre-deployment or post-deployment files.</span></span>  
  
 <span data-ttu-id="f887d-145">자세한 내용은 [Validate a DAC Package](validate-a-dac-package.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f887d-145">For more information, see [Validate a DAC Package](validate-a-dac-package.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f887d-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f887d-146">See Also</span></span>  
 <span data-ttu-id="f887d-147">[데이터 계층 애플리케이션](data-tier-applications.md) </span><span class="sxs-lookup"><span data-stu-id="f887d-147">[Data-tier Applications](data-tier-applications.md) </span></span>  
 <span data-ttu-id="f887d-148">[데이터 계층 애플리케이션 배포](deploy-a-data-tier-application.md) </span><span class="sxs-lookup"><span data-stu-id="f887d-148">[Deploy a Data-tier Application](deploy-a-data-tier-application.md) </span></span>  
 [<span data-ttu-id="f887d-149">데이터 계층 애플리케이션 업그레이드</span><span class="sxs-lookup"><span data-stu-id="f887d-149">Upgrade a Data-tier Application</span></span>](upgrade-a-data-tier-application.md)  
  
  
