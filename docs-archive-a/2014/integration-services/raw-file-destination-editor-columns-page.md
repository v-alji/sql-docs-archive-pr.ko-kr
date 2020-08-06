---
title: 원시 파일 대상 편집기 (열 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationcolumns.f1
ms.assetid: 37f61d0b-1269-42ee-94ab-011cbaac63e9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8a89d8ca46805a23fd03465ed40428081499dccb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729595"
---
# <a name="raw-file-destination-editor-columns-page"></a><span data-ttu-id="c5697-102">원시 파일 대상 편집기(열 페이지)</span><span class="sxs-lookup"><span data-stu-id="c5697-102">Raw File Destination Editor (Columns Page)</span></span>
  <span data-ttu-id="c5697-103">원시 파일 대상 편집기를 사용하여 원시 데이터를 파일에 기록하도록 원시 파일 대상을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-103">Use the Raw File Destination Editor to configure the Raw File destination to write raw data to a file.</span></span>  
  
 <span data-ttu-id="c5697-104">**수행 작업**</span><span class="sxs-lookup"><span data-stu-id="c5697-104">**What do you want to do?**</span></span>  
  
-   [<span data-ttu-id="c5697-105">원시 파일 대상 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="c5697-105">Open the Raw File Destination Editor</span></span>](#open)  
  
-   [<span data-ttu-id="c5697-106">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c5697-106">Set options on the Connection Manager tab</span></span>](#connection)  
  
-   [<span data-ttu-id="c5697-107">열 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c5697-107">Set options on the Columns tab</span></span>](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a><span data-ttu-id="c5697-108">원시 파일 대상 편집기 열기</span><span class="sxs-lookup"><span data-stu-id="c5697-108">Open the Raw File Destination Editor</span></span>  
  
1.  <span data-ttu-id="c5697-109">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 원시 파일 대상을 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]패키지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-109">Add the Raw File destination to an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="c5697-110">구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **편집**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-110">Right-click the component and then click **Edit**.</span></span>  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> <span data-ttu-id="c5697-111">연결 관리자 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c5697-111">Set options on the Connection Manager tab</span></span>  
 <span data-ttu-id="c5697-112">**액세스 모드**</span><span class="sxs-lookup"><span data-stu-id="c5697-112">**Access mode**</span></span>  
 <span data-ttu-id="c5697-113">파일 이름 지정 방법을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-113">Select how the file name is specified.</span></span> <span data-ttu-id="c5697-114">**파일 이름** 을 선택하여 파일 이름 및 경로를 직접 입력하고 **변수를 사용한 파일 이름** 을 선택하여 파일 이름이 포함된 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-114">Select **File name** to enter the file name and path directly, of **File name from variable** to specify a variable that contains the file name.</span></span>  
  
 <span data-ttu-id="c5697-115">**파일 이름** 또는 **변수 이름**</span><span class="sxs-lookup"><span data-stu-id="c5697-115">**File name** or **Variable name**</span></span>  
 <span data-ttu-id="c5697-116">원시 파일의 이름과 경로를 입력하거나 파일 이름이 포함된 변수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-116">Enter the name and path of the raw file, or select the variable that contains the file name.</span></span>  
  
 <span data-ttu-id="c5697-117">**쓰기 옵션**</span><span class="sxs-lookup"><span data-stu-id="c5697-117">**Write option**</span></span>  
 <span data-ttu-id="c5697-118">파일을 만들고 파일에 쓰는 데 사용할 메서드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-118">Select the method used to create and write to the file.</span></span>  
  
 <span data-ttu-id="c5697-119">**초기 원시 파일 생성**</span><span class="sxs-lookup"><span data-stu-id="c5697-119">**Generate initial raw file**</span></span>  
 <span data-ttu-id="c5697-120">패키지를 실행할 필요 없이 열만 포함된 빈 원시 파일(메타데이터 전용 파일)을 생성하려면 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-120">Click the button to generate an empty raw file that contains only the columns (metadata-only file), without having to run the package.</span></span> <span data-ttu-id="c5697-121">원시 파일 원본이 메타데이터 전용 파일을 가리키도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-121">You can point the Raw File source to the metadata-only file.</span></span>  
  
 <span data-ttu-id="c5697-122">단추를 클릭하면 열 목록이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-122">When you click the button, a list of the columns appears.</span></span> <span data-ttu-id="c5697-123">취소를 클릭하고 열을 수정하거나 확인을 클릭하여 파일 만들기를 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-123">You can click cancel and modify the columns or click OK to proceed with creating the file.</span></span>  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a><span data-ttu-id="c5697-124">열 탭에서 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="c5697-124">Set options on the Columns tab</span></span>  
 <span data-ttu-id="c5697-125">**사용 가능한 입력 열**</span><span class="sxs-lookup"><span data-stu-id="c5697-125">**Available Input Columns**</span></span>  
 <span data-ttu-id="c5697-126">원시 파일에 쓸 하나 이상의 입력 열을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-126">Select one or more input columns to write to the raw file.</span></span>  
  
 <span data-ttu-id="c5697-127">**입력 열**</span><span class="sxs-lookup"><span data-stu-id="c5697-127">**Input Column**</span></span>  
 <span data-ttu-id="c5697-128">입력 열은 **사용 가능한 입력 열**에서 선택할 경우 이 테이블에 자동으로 추가되거나 이 테이블에서 입력 열을 직접 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-128">An input column is automatically added to this table when you select it under **Available Input Columns**, or you can select the input column directly in this table.</span></span>  
  
 <span data-ttu-id="c5697-129">**출력 별칭**</span><span class="sxs-lookup"><span data-stu-id="c5697-129">**Output Alias**</span></span>  
 <span data-ttu-id="c5697-130">출력 열에 사용할 대체 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c5697-130">Specify an alternate name to use for the output column.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5697-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c5697-131">See Also</span></span>  
 [<span data-ttu-id="c5697-132">원시 파일 대상</span><span class="sxs-lookup"><span data-stu-id="c5697-132">Raw File Destination</span></span>](data-flow/raw-file-destination.md)  
  
  
