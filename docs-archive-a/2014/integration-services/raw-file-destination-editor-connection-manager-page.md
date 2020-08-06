---
title: 원시 파일 대상 편집기 (연결 관리자 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a693591921a5669eb9bc8160f0be076ab4d6869b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729592"
---
# <a name="raw-file-destination-editor-connection-manager-page"></a><span data-ttu-id="c05ed-102">원시 파일 대상 편집기(연결 관리자 페이지)</span><span class="sxs-lookup"><span data-stu-id="c05ed-102">Raw File Destination Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="c05ed-103">원시 파일 대상 편집기를 사용하여 원시 데이터를 파일에 기록하도록 원시 파일 대상을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="c05ed-104">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="c05ed-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="c05ed-105">원시 파일 대상 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="c05ed-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   [<span data-ttu-id="c05ed-106">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c05ed-106">Set options on the Connection Manager tab</span></span>](#connection)  
  
-   [<span data-ttu-id="c05ed-107">열 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c05ed-107">Set options on the Columns tab</span></span>](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a><span data-ttu-id="c05ed-108">원시 파일 대상 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="c05ed-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="c05ed-109">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 원시 파일 대상을 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]패키지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="c05ed-110">구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="c05ed-111">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c05ed-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="c05ed-112">**액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="c05ed-112">**Access mode**</span></span>  
 <span data-ttu-id="c05ed-113">파일 이름 지정 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-113">Select how the file name is specified.</span></span> <span data-ttu-id="c05ed-114">**파일 이름** 을 선택하여 파일 이름 및 경로를 직접 입력하고 **변수를 사용한 파일 이름** 을 선택하여 파일 이름이 포함된 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="c05ed-115">**파일 이름** 또는 **변수 이름**</span><span class="sxs-lookup"><span data-stu-id="c05ed-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="c05ed-116">원시 파일의 이름과 경로를 입력하거나 파일 이름이 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="c05ed-117">**쓰기 옵션**</span><span class="sxs-lookup"><span data-stu-id="c05ed-117">**Write option**</span></span>  
 <span data-ttu-id="c05ed-118">파일을 만들고 파일에 쓰는 데 사용할 메서드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="c05ed-119">**초기 원시 파일 생성**</span><span class="sxs-lookup"><span data-stu-id="c05ed-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="c05ed-120">패키지를 실행할 필요 없이 열만 포함된 빈 원시 파일(메타데이터 전용 파일)을 생성하려면 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="c05ed-121">파일에는 **원시 파일 대상 편집기** 의 **열**페이지에서 선택한 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-121">The file contains the columns that you selected on the **Columns** page of the **Raw File Destination Editor**.</span></span> <span data-ttu-id="c05ed-122">원시 파일 원본이 이 메타데이터 전용 파일을 가리키도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-122">You can point the Raw File source to this metadata-only file.</span></span>  
  
 <span data-ttu-id="c05ed-123">**초기 원시 파일 생성**을 누르면 메시지 상자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-123">When you click **Generate initial raw file**, a message box appears.</span></span> <span data-ttu-id="c05ed-124">**확인** 을 클릭하여 파일 만들기를 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-124">Click **OK** to proceed with creating the file.</span></span> <span data-ttu-id="c05ed-125">**열** 페이지의 서로 다른 열 목록을 선택하려면 **취소** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-125">Click **Cancel** to select a different list of columns on the **Columns** page.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="c05ed-126">열 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c05ed-126">Set options on the Columns tab</span></span>  
 <span data-ttu-id="c05ed-127">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="c05ed-127">**Available Input Columns**</span></span>  
 <span data-ttu-id="c05ed-128">원시 파일에 쓸 하나 이상의 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-128">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="c05ed-129">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="c05ed-129">**Input Column**</span></span>  
 <span data-ttu-id="c05ed-130">입력 열은 **사용 가능한 입력 열**에서 선택할 경우 이 테이블에 자동으로 추가되거나 이 테이블에서 입력 열을 직접 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-130">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="c05ed-131">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="c05ed-131">**Output Alias**</span></span>  
 <span data-ttu-id="c05ed-132">출력 열에 사용할 대체 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c05ed-132">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05ed-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c05ed-133">See Also</span></span>  
 [<span data-ttu-id="c05ed-134">원시 파일 대상</span><span class="sxs-lookup"><span data-stu-id="c05ed-134">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
