---
title: '4단계: 플랫 파일 대상 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f4088de3-16d8-419c-96a1-a2cd005d0a5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: eff65f4a94a412d55af8055e302195f87ae4cdb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735471"
---
# <a name="step-4-adding-a-flat-file-destination"></a><span data-ttu-id="d2d8c-102">4단계: 플랫 파일 대상 추가</span><span class="sxs-lookup"><span data-stu-id="d2d8c-102">Step 4: Adding a Flat File Destination</span></span>
  <span data-ttu-id="d2d8c-103">Lookup Currency Key 변환의 오류 출력은 조회 작업에 실패한 모든 데이터 행을 스크립트 변환으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-103">The error output of the Lookup Currency Key transformation redirects to the Script transformation any data rows that failed the lookup operation.</span></span> <span data-ttu-id="d2d8c-104">발생한 오류에 대한 정보를 보강하기 위해 스크립트 변환은 오류에 대한 설명을 가져오는 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-104">To enhance information about the errors that occurred, the Script transformation runs a script that gets the description of errors.</span></span>  
  
 <span data-ttu-id="d2d8c-105">이 태스크에서는 나중에 처리할 수 있도록 실패한 행에 대한 이러한 모든 정보를 구분된 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-105">In this task, you will save all this information about the failed rows to a delimited file for later processing.</span></span> <span data-ttu-id="d2d8c-106">실패한 행을 저장하려면 오류 데이터를 포함할 텍스트 파일에 대해 플랫 파일 연결 관리자를 추가 및 구성하고 플랫 파일 대상을 추가 및 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-106">To save the failed rows, you must add and configure a Flat File connection manager for the text file that will contain the error data and a Flat File destination.</span></span> <span data-ttu-id="d2d8c-107">플랫 파일 대상에서 사용되는 플랫 파일 연결 관리자에 속성을 설정하여 플랫 파일 대상에서 텍스트 파일을 기록하고 형식을 지정하는 방식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-107">By setting properties on the Flat File connection manager that the Flat File destination uses, you can specify how the Flat File destination formats and writes the text file.</span></span> <span data-ttu-id="d2d8c-108">자세한 내용은 [Flat File Connection Manager](connection-manager/file-connection-manager.md) 및 [flat file Destination](data-flow/flat-file-destination.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-108">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md) and [Flat File Destination](data-flow/flat-file-destination.md).</span></span>  
  
### <a name="to-add-and-configure-a-flat-file-destination"></a><span data-ttu-id="d2d8c-109">플랫 파일 대상을 추가하고 구성하려면</span><span class="sxs-lookup"><span data-stu-id="d2d8c-109">To add and configure a Flat File destination</span></span>  
  
1.  <span data-ttu-id="d2d8c-110">**데이터 흐름** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-110">Click the **Data Flow** tab.</span></span>  
  
2.  <span data-ttu-id="d2d8c-111">**SSIS 도구 상자**에서 **기타**를 확장하고 **플랫 파일 대상** 을 데이터 흐름 디자인 화면에 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-111">In the **SSIS Toolbox**, expand **Other**, and drag **Flat File Destination** onto the data flow design surface.</span></span> <span data-ttu-id="d2d8c-112">**플랫 파일 대상** 을 **Get Error Description** 변환 바로 아래에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-112">Put the **Flat File Destination** directly underneath the **Get Error Description** transformation.</span></span>  
  
3.  <span data-ttu-id="d2d8c-113">**Get Error Description** 변환을 클릭한 다음 녹색 화살표를 새 **플랫 파일 대상**에 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-113">Click the **Get Error Description** transformation, and then drag the green arrow onto the new **Flat File Destination**.</span></span>  
  
4.  <span data-ttu-id="d2d8c-114">**데이터 흐름** 디자인 화면에서 새로 추가한 **플랫 파일 대상** 변환의 **플랫 파일 대상** 을 클릭한 다음 이름을 **Failed Rows**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-114">On the **Data Flow** design surface, click **Flat File Destination** in the newly added **Flat File Destination** transformation, and change the name to **Failed Rows**.</span></span>  
  
5.  <span data-ttu-id="d2d8c-115">**Failed Rows** 변환을 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭한 다음 **플랫 파일 대상 편집기**에서 **새로 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-115">Right-click the **Failed Rows** transformation, click **Edit**, and then in the **Flat File Destination Editor**, click **New**.</span></span>  
  
6.  <span data-ttu-id="d2d8c-116">**플랫 파일 형식** 대화 상자에서 **구분 기호로 분리됨** 을 선택했는지 확인한 다음 **확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-116">In the **Flat File Format** dialog box, verify that **Delimited** is selected, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="d2d8c-117">**플랫 파일 연결 관리자 편집기**의 **연결 관리자 이름** 상자에을 입력 `Error Data` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-117">In the **Flat File Connection Manager Editor**, in the **Connection Manager Name** box type `Error Data`.</span></span>  
  
8.  <span data-ttu-id="d2d8c-118">**플랫 파일 연결 관리자 편집기** 대화 상자에서 **찾아보기**를 클릭한 다음 파일을 저장할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-118">In the **Flat File Connection Manager Editor** dialog box, click **Browse**, and locate the folder in which to store the file.</span></span>  
  
9. <span data-ttu-id="d2d8c-119">**열기** 대화 상자에서 **파일 이름**에를 입력 한 `ErrorOutput.txt` 다음 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-119">In the **Open** dialog box, for **File name**, type `ErrorOutput.txt`, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="d2d8c-120">**플랫 파일 연결 관리자 편집기** 대화 상자에서 **로캘** 상자에 영어(미국), **코드 페이지** 에 1252(ANSI - 라틴어 I)가 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-120">In the **Flat File Connection Manager Editor** dialog box, verify that the **Locale** box contains English (United States) and **Code page** contains 1252 (ANSI -Latin I).</span></span>  
  
11. <span data-ttu-id="d2d8c-121">옵션 창에서 **열**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-121">In the options pane, click **Columns**.</span></span>  
  
     <span data-ttu-id="d2d8c-122">원본 데이터 파일의 열 외에 새로운 열인 ErrorCode, ErrorColumn 및 ErrorDescription이 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-122">Notice that, in addition to the columns from the source data file, three new columns are present: ErrorCode, ErrorColumn, and ErrorDescription.</span></span> <span data-ttu-id="d2d8c-123">이러한 열은 Lookup Currency Key 변환의 오류 출력 및 Get Error Description 변환의 스크립트에 의해 생성되었으며 해당 열을 사용하여 실패한 행의 원인에 따라 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-123">These columns are generated by the error output of the Lookup Currency Key transformation and by the script in the Get Error Description transformation, and can be used to troubleshoot the cause of the failed row.</span></span>  
  
12. <span data-ttu-id="d2d8c-124">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-124">Click **OK**.</span></span>  
  
13. <span data-ttu-id="d2d8c-125">**플랫 파일 대상 편집기**에서 **파일의 데이터 덮어쓰기** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-125">In the **Flat File Destination Editor**, clear the **Overwrite data in the file** check box.</span></span>  
  
     <span data-ttu-id="d2d8c-126">이 확인란의 선택을 취소하면 여러 패키지 실행 시 오류가 계속 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-126">Clearing this check box persists the errors over multiple package executions.</span></span>  
  
14. <span data-ttu-id="d2d8c-127">**플랫 파일 대상 편집기**에서 **매핑** 을 클릭하여 모든 열이 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-127">In the **Flat File Destination Editor**, click **Mappings** to verify that all the columns are correct.</span></span> <span data-ttu-id="d2d8c-128">대상의 열 이름을 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-128">Optionally, you can rename the columns in the destination.</span></span>  
  
15. <span data-ttu-id="d2d8c-129">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d2d8c-129">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d2d8c-130">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d2d8c-130">Next Steps</span></span>  
 [<span data-ttu-id="d2d8c-131">5단계: 4단원 자습서 패키지 테스트</span><span class="sxs-lookup"><span data-stu-id="d2d8c-131">Step 5: Testing the Lesson 4 Tutorial Package</span></span>](../integration-services/lesson-4-5-testing-the-lesson-4-tutorial-package.md)  
  
  
