---
title: 스크립팅 변수와 함께 sqlcmd 사용
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- scripts [SQL Server], sqlcmd utility
- variables [SQL Server], scripts
- scripting variables [SQL Server]
- sqlcmd utility, scripts
- setvar command
ms.assetid: 793495ca-cfc9-498d-8276-c44a5d09a92c
author: rothja
ms.author: jroth
ms.openlocfilehash: 8443cb400dc099726ba75bfcec2d38cee4ee2dff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653805"
---
# <a name="use-sqlcmd-with-scripting-variables"></a><span data-ttu-id="07a26-102">스크립팅 변수와 함께 sqlcmd 사용</span><span class="sxs-lookup"><span data-stu-id="07a26-102">Use sqlcmd with Scripting Variables</span></span>
  <span data-ttu-id="07a26-103">스크립트에서 사용할 수 있는 변수를 스크립팅 변수라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-103">Variables that are used in scripts are called scripting variables.</span></span> <span data-ttu-id="07a26-104">스크립팅 변수를 사용하면 하나의 스크립트를 여러 시나리오에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-104">Scripting variables enable one script to be used in multiple scenarios.</span></span> <span data-ttu-id="07a26-105">예를 들어 하나의 스크립트를 여러 서버에서 실행해야 하는 경우 각 서버에 맞게 스크립트를 수정하는 대신 서버 이름에 스크립팅 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-105">For example, if you want to run one script against multiple servers, instead of modifying the script for each server, you can use a scripting variable for the server name.</span></span> <span data-ttu-id="07a26-106">스크립팅 변수로 제공되는 서버 이름을 변경하여 같은 스크립트를 다른 서버에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-106">By changing the server name supplied to the scripting variable, the same script can be executed on different servers.</span></span>  
  
 <span data-ttu-id="07a26-107">스크립팅 변수는 **setvar** 명령을 사용하여 명시적으로 정의하거나 **sqlcmd-v** 옵션을 사용하여 암시적으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-107">Scripting variables can be defined explicitly by using the **setvar** command, or implicitly by using the **sqlcmd-v** option.</span></span>  
  
 <span data-ttu-id="07a26-108">이 항목에는 **SET**를 사용하여 Cmd.exe 명령 프롬프트에서 환경 변수를 정의하는 예도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-108">This topic also includes examples defining environmental variables at the Cmd.exe command prompt by using **SET**.</span></span>  
  
## <a name="setting-scripting-variables-by-using-the-setvar-command"></a><span data-ttu-id="07a26-109">setvar 명령을 사용하여 스크립팅 변수 설정</span><span class="sxs-lookup"><span data-stu-id="07a26-109">Setting Scripting Variables by Using the setvar Command</span></span>  
 <span data-ttu-id="07a26-110">**setvar** 명령은 스크립팅 변수를 정의하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-110">The **setvar** command is used to define scripting variables.</span></span> <span data-ttu-id="07a26-111">**setvar** 명령을 사용하여 정의한 변수는 내부적으로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-111">Variables that are defined by using the **setvar** command are stored internally.</span></span> <span data-ttu-id="07a26-112">**SET**를 사용하여 명령 프롬프트에서 정의하는 환경 변수와 스크립팅 변수를 혼동하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-112">Scripting variables should not be confused with environment variables that are defined at the command prompt by using **SET**.</span></span> <span data-ttu-id="07a26-113">스크립트에서 환경 변수가 아니거나 **setvar**을 사용하여 정의되지 않은 변수를 참조하면 오류 메시지가 반환되고 스크립트 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-113">If a script references a variable that is not an environment variable or is not defined by using **setvar**, an error message is returned and the execution of the script will stop.</span></span> <span data-ttu-id="07a26-114">자세한 내용은 **sqlcmd 유틸리티** 의 [-b](../../tools/sqlcmd-utility.md)옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="07a26-114">For more information, see the **-b** option in [sqlcmd Utility](../../tools/sqlcmd-utility.md).</span></span>  
  
## <a name="variable-precedence-low-to-high"></a><span data-ttu-id="07a26-115">변수 우선 순위(낮은 순위에서 높은 순위)</span><span class="sxs-lookup"><span data-stu-id="07a26-115">Variable Precedence (Low to High)</span></span>  
 <span data-ttu-id="07a26-116">같은 이름의 변수 유형이 둘 이상인 경우 우선 순위가 가장 높은 변수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-116">If more than one type of variable has the same name, the variable with the highest precedence is used.</span></span>  
  
1.  <span data-ttu-id="07a26-117">시스템 수준 환경 변수</span><span class="sxs-lookup"><span data-stu-id="07a26-117">System level environmental variables</span></span>  
  
2.  <span data-ttu-id="07a26-118">사용자 수준 환경 변수</span><span class="sxs-lookup"><span data-stu-id="07a26-118">User level environmental variables</span></span>  
  
3.  <span data-ttu-id="07a26-119">**SET X=Y**를 시작하기 전에 명령 프롬프트에서 설정된 명령 셸( **SET X=Y**)</span><span class="sxs-lookup"><span data-stu-id="07a26-119">Command shell (**SET X=Y**) set at command prompt before starting **sqlcmd**</span></span>  
  
4.  <span data-ttu-id="07a26-120">**sqlcmd-v** X=Y</span><span class="sxs-lookup"><span data-stu-id="07a26-120">**sqlcmd-v** X=Y</span></span>  
  
5.  <span data-ttu-id="07a26-121">**:Setvar** X Y</span><span class="sxs-lookup"><span data-stu-id="07a26-121">**:Setvar** X Y</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="07a26-122">환경 변수를 보려면 **제어판**에서 **시스템**을 연 다음 **고급** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-122">To view the environmental variables, in **Control Panel**, open **System**, and then click the **Advanced** tab.</span></span>  
  
## <a name="implicitly-setting-scripting-variables"></a><span data-ttu-id="07a26-123">암시적 스크립팅 변수 설정</span><span class="sxs-lookup"><span data-stu-id="07a26-123">Implicitly Setting Scripting Variables</span></span>  
 <span data-ttu-id="07a26-124">관련 **sqlcmd** 변수가 있는 옵션을 사용하여 **sqlcmd** 를 시작하면 **sqlcmd** 변수는 옵션을 사용하여 지정한 값으로 암시적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-124">When you start **sqlcmd** with an option that has a related **sqlcmd** variable, the **sqlcmd** variable is set implicitly to the value that is specified by using the option.</span></span> <span data-ttu-id="07a26-125">다음 예에서는 `sqlcmd` 를 `-l` 옵션으로 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-125">In the following example, `sqlcmd` is started with the `-l` option.</span></span> <span data-ttu-id="07a26-126">이 경우 암시적으로 SQLLOGINTIMEOUT 변수가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-126">This implicitly sets the SQLLOGINTIMEOUT variable.</span></span>  
  
 `c:\> sqlcmd -l 60`  
  
 <span data-ttu-id="07a26-127">**-v** 옵션을 사용하여 스크립트에 있는 스크립팅 변수를 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-127">You can also use the **-v** option to set a scripting variable that exists in a script.</span></span> <span data-ttu-id="07a26-128">파일 이름이 `testscript.sql`인 다음 스크립트에서 `ColumnName` 이 스크립팅 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-128">In the following script (the file name is `testscript.sql`), `ColumnName` is a scripting variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `SELECT x.$(ColumnName)`  
  
 `FROM Person.Person x`  
  
 <span data-ttu-id="07a26-129">`WHERE c.`BusinessEntityID `< 5;`</span><span class="sxs-lookup"><span data-stu-id="07a26-129">`WHERE c.`BusinessEntityID `< 5;`</span></span>  
  
 <span data-ttu-id="07a26-130">다음과 같이 `-v` 옵션을 사용하여 반환하려는 열의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-130">You can then specify the name of the column that you want returned by using the `-v` option:</span></span>  
  
 `sqlcmd -v ColumnName ="FirstName" -i c:\testscript.sql`  
  
 <span data-ttu-id="07a26-131">같은 스크립트를 사용하여 다른 열을 반환하려면 `ColumnName` 스크립팅 변수 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-131">To return a different column by using the same script, change the value of the `ColumnName` scripting variable.</span></span>  
  
 `sqlcmd -v ColumnName ="LastName" -i c:\testscript.sql`  
  
## <a name="guidelines-for-scripting-variable-names-and-values"></a><span data-ttu-id="07a26-132">스크립팅 변수 이름 및 값에 대한 지침</span><span class="sxs-lookup"><span data-stu-id="07a26-132">Guidelines for Scripting Variable Names and Values</span></span>  
 <span data-ttu-id="07a26-133">스크립팅 변수의 이름을 지정하는 경우 다음 지침을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-133">Consider the following guidelines when you name scripting variables:</span></span>  
  
-   <span data-ttu-id="07a26-134">변수 이름은 공백 문자나 따옴표를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-134">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="07a26-135">변수 이름은 *$(var)* 와 같은 변수 식 형태가 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-135">Variable names must not have the same form as a variable expression, such as *$(var)*.</span></span>  
  
-   <span data-ttu-id="07a26-136">스크립팅 변수는 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-136">Scripting variables are case-insensitive</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07a26-137">**sqlcmd** 환경 변수에 값을 지정하지 않으면 변수가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-137">If no value is assigned to a **sqlcmd** environment variable, the variable is removed.</span></span> <span data-ttu-id="07a26-138">값이 없는 **:setvar VarName** 을 사용하면 변수가 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-138">Using **:setvar VarName** without a value clears the variable.</span></span>  
  
 <span data-ttu-id="07a26-139">스크립팅 변수의 값을 지정하는 경우 다음 지침을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-139">Consider the following guidelines when you specify values for scripting variables:</span></span>  
  
-   <span data-ttu-id="07a26-140">문자열 값에 공백이 포함된 경우 **setvar** 또는 **-v** 옵션을 사용하여 정의한 변수 값을 따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-140">Variable values that are defined by using **setvar** or the **-v** option must be enclosed by quotation marks if the string value contains spaces.</span></span>  
  
-   <span data-ttu-id="07a26-141">변수 값에 따옴표가 포함되는 경우 따옴표를 이스케이프 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-141">If quotation marks are part of the variable value, they must be escaped.</span></span> <span data-ttu-id="07a26-142">예를 들면 :`setvar MyVar "spac""e"`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-142">For example: :`setvar MyVar "spac""e"`.</span></span>  
  
## <a name="guidelines-for-cmdexe-set-variable-values-and-names"></a><span data-ttu-id="07a26-143">Cmd.exe SET 변수 값 및 이름에 대한 지침</span><span class="sxs-lookup"><span data-stu-id="07a26-143">Guidelines for Cmd.exe SET Variable Values and Names</span></span>  
 <span data-ttu-id="07a26-144">SET를 사용하여 정의한 변수는 Cmd.exe 환경의 일부이며 **sqlcmd**에서 참조될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-144">Variables that are defined by using SET are part of the Cmd.exe environment and can be referenced by **sqlcmd**.</span></span> <span data-ttu-id="07a26-145">다음 지침을 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="07a26-145">Consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="07a26-146">변수 이름은 공백 문자나 따옴표를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-146">Variable names must not contain white space characters or quotation marks.</span></span>  
  
-   <span data-ttu-id="07a26-147">변수 값은 공백이나 따옴표를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-147">Variable values may contain spaces or quotation marks.</span></span>  
  
## <a name="sqlcmd-scripting-variables"></a><span data-ttu-id="07a26-148">sqlcmd 스크립팅 변수</span><span class="sxs-lookup"><span data-stu-id="07a26-148">sqlcmd Scripting Variables</span></span>  
 <span data-ttu-id="07a26-149">**sqlcmd** 에서 정의하는 변수를 스크립팅 변수라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-149">Variables that are defined by **sqlcmd** are known as scripting variables.</span></span> <span data-ttu-id="07a26-150">다음 표에는 **sqlcmd** 스크립팅 변수가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-150">The following table lists **sqlcmd** scripting variables.</span></span>  
  
|<span data-ttu-id="07a26-151">변수</span><span class="sxs-lookup"><span data-stu-id="07a26-151">Variable</span></span>|<span data-ttu-id="07a26-152">관련 옵션</span><span class="sxs-lookup"><span data-stu-id="07a26-152">Related option</span></span>|<span data-ttu-id="07a26-153">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-153">R/W</span></span>|<span data-ttu-id="07a26-154">기본값</span><span class="sxs-lookup"><span data-stu-id="07a26-154">Default</span></span>|  
|--------------|--------------------|----------|-------------|  
|<span data-ttu-id="07a26-155">SQLCMDUSER\*</span><span class="sxs-lookup"><span data-stu-id="07a26-155">SQLCMDUSER\*</span></span>|<span data-ttu-id="07a26-156">-U</span><span class="sxs-lookup"><span data-stu-id="07a26-156">-U</span></span>|<span data-ttu-id="07a26-157">R</span><span class="sxs-lookup"><span data-stu-id="07a26-157">R</span></span>|<span data-ttu-id="07a26-158">""</span><span class="sxs-lookup"><span data-stu-id="07a26-158">""</span></span>|  
|<span data-ttu-id="07a26-159">SQLCMDPASSWORD\*</span><span class="sxs-lookup"><span data-stu-id="07a26-159">SQLCMDPASSWORD\*</span></span>|<span data-ttu-id="07a26-160">-P</span><span class="sxs-lookup"><span data-stu-id="07a26-160">-P</span></span>|--|<span data-ttu-id="07a26-161">""</span><span class="sxs-lookup"><span data-stu-id="07a26-161">""</span></span>|  
|<span data-ttu-id="07a26-162">SQLCMDSERVER\*</span><span class="sxs-lookup"><span data-stu-id="07a26-162">SQLCMDSERVER\*</span></span>|<span data-ttu-id="07a26-163">-S</span><span class="sxs-lookup"><span data-stu-id="07a26-163">-S</span></span>|<span data-ttu-id="07a26-164">R</span><span class="sxs-lookup"><span data-stu-id="07a26-164">R</span></span>|<span data-ttu-id="07a26-165">"DefaultLocalInstance"</span><span class="sxs-lookup"><span data-stu-id="07a26-165">"DefaultLocalInstance"</span></span>|  
|<span data-ttu-id="07a26-166">SQLCMDWORKSTATION</span><span class="sxs-lookup"><span data-stu-id="07a26-166">SQLCMDWORKSTATION</span></span>|<span data-ttu-id="07a26-167">-H</span><span class="sxs-lookup"><span data-stu-id="07a26-167">-H</span></span>|<span data-ttu-id="07a26-168">R</span><span class="sxs-lookup"><span data-stu-id="07a26-168">R</span></span>|<span data-ttu-id="07a26-169">"ComputerName"</span><span class="sxs-lookup"><span data-stu-id="07a26-169">"ComputerName"</span></span>|  
|<span data-ttu-id="07a26-170">SQLCMDDBNAME</span><span class="sxs-lookup"><span data-stu-id="07a26-170">SQLCMDDBNAME</span></span>|<span data-ttu-id="07a26-171">-d</span><span class="sxs-lookup"><span data-stu-id="07a26-171">-d</span></span>|<span data-ttu-id="07a26-172">R</span><span class="sxs-lookup"><span data-stu-id="07a26-172">R</span></span>|<span data-ttu-id="07a26-173">""</span><span class="sxs-lookup"><span data-stu-id="07a26-173">""</span></span>|  
|<span data-ttu-id="07a26-174">SQLCMDLOGINTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07a26-174">SQLCMDLOGINTIMEOUT</span></span>|<span data-ttu-id="07a26-175">-l</span><span class="sxs-lookup"><span data-stu-id="07a26-175">-l</span></span>|<span data-ttu-id="07a26-176">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-176">R/W</span></span>|<span data-ttu-id="07a26-177">"8"(초)</span><span class="sxs-lookup"><span data-stu-id="07a26-177">"8" (seconds)</span></span>|  
|<span data-ttu-id="07a26-178">SQLCMDSTATTIMEOUT</span><span class="sxs-lookup"><span data-stu-id="07a26-178">SQLCMDSTATTIMEOUT</span></span>|<span data-ttu-id="07a26-179">-t</span><span class="sxs-lookup"><span data-stu-id="07a26-179">-t</span></span>|<span data-ttu-id="07a26-180">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-180">R/W</span></span>|<span data-ttu-id="07a26-181">"0" = 무기한 대기</span><span class="sxs-lookup"><span data-stu-id="07a26-181">"0" = wait indefinitely</span></span>|  
|<span data-ttu-id="07a26-182">SQLCMDHEADERS</span><span class="sxs-lookup"><span data-stu-id="07a26-182">SQLCMDHEADERS</span></span>|<span data-ttu-id="07a26-183">-H</span><span class="sxs-lookup"><span data-stu-id="07a26-183">-h</span></span>|<span data-ttu-id="07a26-184">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-184">R/W</span></span>|<span data-ttu-id="07a26-185">"0"</span><span class="sxs-lookup"><span data-stu-id="07a26-185">"0"</span></span>|  
|<span data-ttu-id="07a26-186">SQLCMDCOLSEP</span><span class="sxs-lookup"><span data-stu-id="07a26-186">SQLCMDCOLSEP</span></span>|<span data-ttu-id="07a26-187">-S</span><span class="sxs-lookup"><span data-stu-id="07a26-187">-s</span></span>|<span data-ttu-id="07a26-188">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-188">R/W</span></span>|<span data-ttu-id="07a26-189">" "</span><span class="sxs-lookup"><span data-stu-id="07a26-189">" "</span></span>|  
|<span data-ttu-id="07a26-190">SQLCMDCOLWIDTH</span><span class="sxs-lookup"><span data-stu-id="07a26-190">SQLCMDCOLWIDTH</span></span>|<span data-ttu-id="07a26-191">-w</span><span class="sxs-lookup"><span data-stu-id="07a26-191">-w</span></span>|<span data-ttu-id="07a26-192">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-192">R/W</span></span>|<span data-ttu-id="07a26-193">"0"</span><span class="sxs-lookup"><span data-stu-id="07a26-193">"0"</span></span>|  
|<span data-ttu-id="07a26-194">SQLCMDPACKETSIZE</span><span class="sxs-lookup"><span data-stu-id="07a26-194">SQLCMDPACKETSIZE</span></span>|<span data-ttu-id="07a26-195">지정하지 않을 경우</span><span class="sxs-lookup"><span data-stu-id="07a26-195">-a</span></span>|<span data-ttu-id="07a26-196">R</span><span class="sxs-lookup"><span data-stu-id="07a26-196">R</span></span>|<span data-ttu-id="07a26-197">"4096"</span><span class="sxs-lookup"><span data-stu-id="07a26-197">"4096"</span></span>|  
|<span data-ttu-id="07a26-198">SQLCMDERRORLEVEL</span><span class="sxs-lookup"><span data-stu-id="07a26-198">SQLCMDERRORLEVEL</span></span>|<span data-ttu-id="07a26-199">-M</span><span class="sxs-lookup"><span data-stu-id="07a26-199">-m</span></span>|<span data-ttu-id="07a26-200">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-200">R/W</span></span>|<span data-ttu-id="07a26-201">"0"</span><span class="sxs-lookup"><span data-stu-id="07a26-201">"0"</span></span>|  
|<span data-ttu-id="07a26-202">SQLCMDMAXVARTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="07a26-202">SQLCMDMAXVARTYPEWIDTH</span></span>|<span data-ttu-id="07a26-203">-y</span><span class="sxs-lookup"><span data-stu-id="07a26-203">-y</span></span>|<span data-ttu-id="07a26-204">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-204">R/W</span></span>|<span data-ttu-id="07a26-205">"256"</span><span class="sxs-lookup"><span data-stu-id="07a26-205">"256"</span></span>|  
|<span data-ttu-id="07a26-206">SQLCMDMAXFIXEDTYPEWIDTH</span><span class="sxs-lookup"><span data-stu-id="07a26-206">SQLCMDMAXFIXEDTYPEWIDTH</span></span>|<span data-ttu-id="07a26-207">-y</span><span class="sxs-lookup"><span data-stu-id="07a26-207">-Y</span></span>|<span data-ttu-id="07a26-208">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-208">R/W</span></span>|<span data-ttu-id="07a26-209">"0" = 제한 없음</span><span class="sxs-lookup"><span data-stu-id="07a26-209">"0" = unlimited</span></span>|  
|<span data-ttu-id="07a26-210">SQLCMDEDITOR</span><span class="sxs-lookup"><span data-stu-id="07a26-210">SQLCMDEDITOR</span></span>||<span data-ttu-id="07a26-211">R/W</span><span class="sxs-lookup"><span data-stu-id="07a26-211">R/W</span></span>|<span data-ttu-id="07a26-212">"edit.com"</span><span class="sxs-lookup"><span data-stu-id="07a26-212">"edit.com"</span></span>|  
|<span data-ttu-id="07a26-213">SQLCMDINI</span><span class="sxs-lookup"><span data-stu-id="07a26-213">SQLCMDINI</span></span>||<span data-ttu-id="07a26-214">R</span><span class="sxs-lookup"><span data-stu-id="07a26-214">R</span></span>|<span data-ttu-id="07a26-215">""</span><span class="sxs-lookup"><span data-stu-id="07a26-215">""</span></span>|  
  
 <span data-ttu-id="07a26-216">\*SQLCMDUSER, SQLCMDPASSWORD 및 SQLCMDSERVER는 **: Connect** 가 사용 될 때 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-216">\* SQLCMDUSER, SQLCMDPASSWORD and SQLCMDSERVER are set when **:Connect** is used.</span></span>  
  
 <span data-ttu-id="07a26-217">R은 값이 프로그램 초기화 시 한 번만 설정될 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-217">R indicates the value can only be set one time during program initialization.</span></span>  
  
 <span data-ttu-id="07a26-218">R/W는 **setvar** 명령을 사용하여 값을 다시 설정할 수 있으며 후속 명령에 새 값이 사용됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-218">R/W indicates that the value can be reset by using the **setvar** command and subsequent commands will use the new value.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="07a26-219">예</span><span class="sxs-lookup"><span data-stu-id="07a26-219">Examples</span></span>  
  
### <a name="a-using-the-setvar-command-in-a-script"></a><span data-ttu-id="07a26-220">A.</span><span class="sxs-lookup"><span data-stu-id="07a26-220">A.</span></span> <span data-ttu-id="07a26-221">스크립트에서 setvar 명령 사용</span><span class="sxs-lookup"><span data-stu-id="07a26-221">Using the setvar command in a script</span></span>  
 <span data-ttu-id="07a26-222">**setvar** 명령을 사용하면 스크립트에서 여러 **sqlcmd** 옵션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-222">Many **sqlcmd** options can be controlled in a script by using the **setvar** command.</span></span> <span data-ttu-id="07a26-223">다음 예에서는 `test.sql` 변수가 `SQLCMDLOGINTIMEOUT` 초로 설정되고 다른 스크립팅 변수인 `60` 가 `server`로 설정된 `testserver`스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-223">In the following example, the script `test.sql` is created in which the `SQLCMDLOGINTIMEOUT` variable is set to `60` seconds and another scripting variable, `server`, is set to `testserver`.</span></span> <span data-ttu-id="07a26-224">`test.sql`의 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-224">The following code is in `test.sql`.</span></span>  
  
 `:setvar SQLCMDLOGINTIMEOUT 60`  
  
 `:setvar server "testserver"`  
  
 `:connect $(server) -l $(SQLCMDLOGINTIMEOUT)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `The script is then called by using sqlcmd:`  
  
 `sqlcmd -i c:\test.sql`  
  
### <a name="b-using-the-setvar-command-interactively"></a><span data-ttu-id="07a26-225">B.</span><span class="sxs-lookup"><span data-stu-id="07a26-225">B.</span></span> <span data-ttu-id="07a26-226">대화식으로 setvar 명령 사용</span><span class="sxs-lookup"><span data-stu-id="07a26-226">Using the setvar command interactively</span></span>  
 <span data-ttu-id="07a26-227">다음 예에서는 `setvar` 명령을 사용하여 대화식으로 스크립팅 변수를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-227">The following example shows how to set a scripting variable interactively by using the `setvar` command.</span></span>  
  
 `sqlcmd`  
  
 `:setvar  MYDATABASE AdventureWorks2012`  
  
 `USE $(MYDATABASE);`  
  
 `GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Changed database context to 'AdventureWorks2012'`  
  
 `1>`  
  
### <a name="c-using-command-prompt-environment-variables-within-sqlcmd"></a><span data-ttu-id="07a26-228">C.</span><span class="sxs-lookup"><span data-stu-id="07a26-228">C.</span></span> <span data-ttu-id="07a26-229">sqlcmd 내에서 명령 프롬프트 환경 변수 사용</span><span class="sxs-lookup"><span data-stu-id="07a26-229">Using command prompt environment variables within sqlcmd</span></span>  
 <span data-ttu-id="07a26-230">다음 예에서는 환경 변수 4개를 `are` 다음 `sqlcmd`에서 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-230">In the following example, four environment variables `are` set and then called from `sqlcmd`.</span></span>  
  
 `C:\>SET tablename=Person.Person`  
  
 `C:\>SET col1=FirstName`  
  
 `C:\>SET col2=LastName`  
  
 `C:\>SET title=Ms.`  
  
 `C:\>sqlcmd -d AdventureWorks2012`  
  
 `1> SELECT TOP 5 $(col1) + ' ' + $(col2) AS Name`  
  
 `2> FROM $(tablename)`  
  
 `3> WHERE Title ='$(title)'`  
  
 `4> GO`  
  
### <a name="d-using-user-level-environment-variables-within-sqlcmd"></a><span data-ttu-id="07a26-231">D.</span><span class="sxs-lookup"><span data-stu-id="07a26-231">D.</span></span> <span data-ttu-id="07a26-232">sqlcmd 내에서 사용자 수준 환경 변수 사용</span><span class="sxs-lookup"><span data-stu-id="07a26-232">Using user-level environment variables within sqlcmd</span></span>  
 <span data-ttu-id="07a26-233">다음 예에서는 명령 프롬프트에서 사용자 수준 환경 변수인 `%Temp%` 를 설정하고 `sqlcmd` 입력 파일로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-233">In the following example the user-level environmental variable `%Temp%` is set at the command prompt and passed to the `sqlcmd` input file.</span></span> <span data-ttu-id="07a26-234">사용자 수준 환경 변수를 얻으려면 **제어판**에서 **시스템**을 두 번 클릭하고</span><span class="sxs-lookup"><span data-stu-id="07a26-234">To obtain the user-level environment variable, in **Control Panel**, double-click **System**.</span></span> <span data-ttu-id="07a26-235">**고급** 탭을 클릭한 다음 **환경 변수**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-235">Click the **Advance** tab, and then click **Environment Variables**.</span></span>  
  
 <span data-ttu-id="07a26-236">입력 파일 `c:\testscript.txt`의 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-236">The following code is in the input file `c:\testscript.txt`:</span></span>  
  
 `:OUT $(MyTempDirectory)`  
  
 `USE AdventureWorks2012;`  
  
 `SELECT FirstName`  
  
 `FROM AdventureWorks2012.Person.Person`  
  
 <span data-ttu-id="07a26-237">`WHERE BusinessEntityID` `< 5;`</span><span class="sxs-lookup"><span data-stu-id="07a26-237">`WHERE BusinessEntityID` `< 5;`</span></span>  
  
 <span data-ttu-id="07a26-238">명령 프롬프트에서 입력되는 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-238">This following code is entered at the command prompt:</span></span>  
  
 `C:\ >SET MyTempDirectory=%Temp%\output.txt`  
  
 `C:\ >sqlcmd -i C:\testscript.txt`  
  
 <span data-ttu-id="07a26-239">출력 파일 C:\Documents and Settings\\<user\>\Local Settings\Temp\output.txt로 보내지는 결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-239">The following result is sent to the output file C:\Documents and Settings\\<user\>\Local Settings\Temp\output.txt.</span></span>  
  
 `Changed database context to 'AdventureWorks2012'.`  
  
 `FirstName`  
  
 `--------------------------------------------------`  
  
 `Gustavo`  
  
 `Catherine`  
  
 `Kim`  
  
 `Humberto`  
  
 `(4 rows affected)`  
  
### <a name="e-using-a-startup-script"></a><span data-ttu-id="07a26-240">E.</span><span class="sxs-lookup"><span data-stu-id="07a26-240">E.</span></span> <span data-ttu-id="07a26-241">시작 스크립트 사용</span><span class="sxs-lookup"><span data-stu-id="07a26-241">Using a startup script</span></span>  
 <span data-ttu-id="07a26-242">**sqlcmd** 시작 스크립트는 **sqlcmd** 가 시작될 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-242">A **sqlcmd** startup script is executed when **sqlcmd** is started.</span></span> <span data-ttu-id="07a26-243">다음 예에서는 `SQLCMDINI`환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-243">The following example sets the environment variable `SQLCMDINI`.</span></span> <span data-ttu-id="07a26-244">다음은 `init.sql.`</span><span class="sxs-lookup"><span data-stu-id="07a26-244">This is the contents of `init.sql.`</span></span>  
  
 `SET NOCOUNT ON`  
  
 `GO`  
  
 `DECLARE @nt_username nvarchar(128)`  
  
 `SET @nt_username = (SELECT rtrim(convert(nvarchar(128), nt_username))`  
  
 `FROM sys.dm_exec_sessions WHERE spid = @@SPID)`  
  
 `SELECT  @nt_username + ' is connected to ' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('servername'))) +`  
  
 `' (' +`  
  
 `rtrim(CONVERT(nvarchar(20), SERVERPROPERTY('productversion'))) +`  
  
 `')'`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH 100`  
  
 `SET NOCOUNT OFF`  
  
 `GO`  
  
 `:setvar SQLCMDMAXFIXEDTYPEWIDTH`  
  
 <span data-ttu-id="07a26-245">다음은 `init.sql` 가 시작될 때 `sqlcmd` 파일을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-245">This calls the `init.sql` file when `sqlcmd` is started.</span></span>  
  
 `C:\> SET sqlcmdini=c:\init.sql`  
  
 `>1 Sqlcmd`  
  
 <span data-ttu-id="07a26-246">다음은 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-246">This is the output.</span></span>  
  
 `>1 < user > is connected to < server > (9.00.2047.00)`  
  
> [!NOTE]  
>  <span data-ttu-id="07a26-247">**-X** 옵션은 시작 스크립트 기능을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-247">The **-X** option disables the startup script feature.</span></span>  
  
### <a name="f-variable-expansion"></a><span data-ttu-id="07a26-248">F.</span><span class="sxs-lookup"><span data-stu-id="07a26-248">F.</span></span> <span data-ttu-id="07a26-249">변수 확장</span><span class="sxs-lookup"><span data-stu-id="07a26-249">Variable expansion</span></span>  
 <span data-ttu-id="07a26-250">다음 예에서는 **sqlcmd** 변수 형식의 데이터로 작업하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-250">The following example shows working with data in the form of a **sqlcmd** variable.</span></span>  
  
 `USE AdventureWorks2012;`  
  
 `CREATE TABLE AdventureWorks2012.dbo.VariableTest`  
  
 `(`  
  
 `Col1 nvarchar(50)`  
  
 `);`  
  
 `GO`  
  
 <span data-ttu-id="07a26-251">`Col1` 값을 포함하는 `dbo.VariableTest` 의 `$(tablename)`에 하나의 행을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-251">Insert one row into `Col1` of `dbo.VariableTest` that contains the value `$(tablename)`.</span></span>  
  
 `INSERT INTO AdventureWorks2012.dbo.VariableTest(Col1)`  
  
 `VALUES('$(tablename)');`  
  
 `GO`  
  
 <span data-ttu-id="07a26-252">`sqlcmd` 프롬프트에서 `$(tablename)`와 같게 설정된 변수가 없을 경우 다음 문은 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-252">At the `sqlcmd` prompt, when no variable is set equal to `$(tablename)`, the following statements return the row.</span></span>  
  
 `C:\> sqlcmd`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>2 GO`  
  
 `>3 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>4 GO`  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `>1 Col1`  
  
 `>2 ------------------`  
  
 `>3 $(tablename)`  
  
 `>4`  
  
 `>5 (1 rows affected)`  
  
 <span data-ttu-id="07a26-253">`MyVar` 변수가 `$(tablename)`으로 설정된 경우</span><span class="sxs-lookup"><span data-stu-id="07a26-253">Given the variable `MyVar` is set to `$(tablename)`.</span></span>  
  
 `>6 :setvar MyVar $(tablename)`  
  
 <span data-ttu-id="07a26-254">다음 문은 행을 반환하며 "'tablename' 스크립팅 변수가 정의되지 않습니다"라는 메시지도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-254">These statements return the row and also return the message "'tablename' scripting variable not defined."</span></span>  
  
 `>6 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(tablename)';`  
  
 `>7 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(tablename)';`  
  
 `>2 GO`  
  
 <span data-ttu-id="07a26-255">다음 문은 행을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="07a26-255">These statements return the row.</span></span>  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = '$(MyVar)';`  
  
 `>2 GO`  
  
 `>1 SELECT Col1 FROM dbo.VariableTest WHERE Col1 = N'$(MyVar)';`  
  
 `>2 GO`  
  
## <a name="see-also"></a><span data-ttu-id="07a26-256">참고 항목</span><span class="sxs-lookup"><span data-stu-id="07a26-256">See Also</span></span>  
 <span data-ttu-id="07a26-257">[sqlcmd 유틸리티 사용](sqlcmd-use-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="07a26-257">[Use the sqlcmd Utility](sqlcmd-use-the-utility.md) </span></span>  
 <span data-ttu-id="07a26-258">[sqlcmd 유틸리티](../../tools/sqlcmd-utility.md) </span><span class="sxs-lookup"><span data-stu-id="07a26-258">[sqlcmd Utility](../../tools/sqlcmd-utility.md) </span></span>  
 [<span data-ttu-id="07a26-259">명령 프롬프트 유틸리티 참조&#40;데이터베이스 엔진#41;</span><span class="sxs-lookup"><span data-stu-id="07a26-259">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](../../tools/command-prompt-utility-reference-database-engine.md)  
  
  
