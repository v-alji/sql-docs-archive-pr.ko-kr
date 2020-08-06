---
title: VBScript를 사용 하 여 SQL Server 서비스 고급 속성 수정 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- VBScript [WMI]
- modifying SQL Server Service properties
- WMI Provider for Configuration Management, VBScript
ms.assetid: f3c5d981-eaa3-4d34-9b91-37e42636aa81
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2cf722b00a31723b77624c33fef81a82ff0cb926
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660923"
---
# <a name="modify-sql-server-service-advanced-properties-using-vbscript"></a><span data-ttu-id="53595-102">VBScript를 사용하여 SQL Server 서비스 고급 속성 수정</span><span class="sxs-lookup"><span data-stu-id="53595-102">Modify SQL Server Service Advanced Properties using VBScript</span></span>
  <span data-ttu-id="53595-103">이 섹션에서는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 컴퓨터에서 실행 중인 설치 된 인스턴스의 버전을 나열 하는 VBScript 프로그램을 만드는 방법을 설명 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="53595-103">This section describes how to create a VBScript program that lists the version of installed instances of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are running on a computer.</span></span>  
  
 <span data-ttu-id="53595-104">이 코드 예제에서는 컴퓨터에서 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인스턴스와 해당 버전을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-104">The code example lists the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the computer and its version.</span></span>  
  
### <a name="listing-name-and-version-of-installed-instances-of-sql-server"></a><span data-ttu-id="53595-105">SQL Server의 설치된 인스턴스 이름 및 버전 나열</span><span class="sxs-lookup"><span data-stu-id="53595-105">Listing name and version of installed instances of SQL Server</span></span>  
  
1.  <span data-ttu-id="53595-106">텍스트 편집기(예: [!INCLUDE[msCoName](../../includes/msconame-md.md)] 메모장)에서 새 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="53595-106">Open a new document in a text editor, such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] Notepad.</span></span> <span data-ttu-id="53595-107">이 절차 다음에 나오는 코드를 복사하여 확장명이 .vbs인 파일로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-107">Copy the code that follows this procedure and save the file with a .vbs extension.</span></span> <span data-ttu-id="53595-108">이 예제의 경우 test.vbs입니다.</span><span class="sxs-lookup"><span data-stu-id="53595-108">This example is called test.vbs.</span></span>  
  
2.  <span data-ttu-id="53595-109">VBScript `GetObject` 함수를 사용하여 컴퓨터 관리용 WMI 공급자의 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-109">Connect to an instance of the WMI Provider for Computer Management with the VBScript `GetObject` function.</span></span> <span data-ttu-id="53595-110">이 예제에서는 mpc라는 원격 컴퓨터에 연결하지만 로컬 컴퓨터에 연결하는 경우에는 winmgmts:root\Microsoft\SqlServer\ComputerManagement와 같이 컴퓨터 이름을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-110">This example connects to a remote computer named mpc, but omit the computer name to connect to the local computer: winmgmts:root\Microsoft\SqlServer\ComputerManagement.</span></span> <span data-ttu-id="53595-111">`GetObject` 함수에 대한 자세한 내용은 VBScript를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="53595-111">For more information about the `GetObject` function, see the VBScript reference.</span></span>  
  
3.  <span data-ttu-id="53595-112">`InstancesOf` 메서드를 사용하여 서비스 목록을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-112">Use the `InstancesOf` method to enumerate a list of the services.</span></span> <span data-ttu-id="53595-113">`ExecQuery` 메서드 대신 간단한 WQL 쿼리와 `InstancesOf` 메서드를 사용하여 서비스를 열거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53595-113">The services can also be enumerated by using a simple WQL query and an `ExecQuery` method instead of the `InstancesOf` method.</span></span>  
  
4.  <span data-ttu-id="53595-114">`ExecQuery` 메서드와 WQL 쿼리를 사용하여 설치된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름과 버전을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-114">Use the `ExecQuery` method and a WQL query to retrieve the name and version of the installed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
5.  <span data-ttu-id="53595-115">파일을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-115">Save the file.</span></span>  
  
6.  <span data-ttu-id="53595-116">명령 프롬프트에서를 입력 하 여 스크립트를 실행 `cscript test.vbs` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53595-116">Run the script by typing `cscript test.vbs` at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53595-117">예제</span><span class="sxs-lookup"><span data-stu-id="53595-117">Example</span></span>  
  
```  
set wmi = GetObject("WINMGMTS:\\.\root\Microsoft\SqlServer\ComputerManagement12")  
for each prop in wmi.ExecQuery("select * from SqlServiceAdvancedProperty where SQLServiceType = 1 AND PropertyName = 'VERSION'")  
WScript.Echo prop.ServiceName & " " & prop.PropertyName & ": " & prop.PropertyStrValue  
next  
```  
  
  
